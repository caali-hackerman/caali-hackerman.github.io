# NextGen Proxy
## "What is it?"
Heavily refactored/rewritten proxy core that
- adds a ton of features for module developers
- gets rid of legacy shit
- gives proxy a performance boost
- prepares proxy for the future (graphical user interface instead of console window, module management/installation built-in, etc)


## "When will it be released?"
Before christmas.


## "But I want to test it already!"
- **!!! SOME MODS MIGHT NOT WORK !!!**
- **!!! ONLY DO THIS IF YOU KINDA KNOW YOUR WAY AROUND A COMPUTER !!!**
- **!!! SUPPORT FOR NEXTGEN TESTING WILL BE LIMITED !!!**
- **!!! IF YOU FIND ANY BUG OR BROKEN MODULE, PLEASE REPORT IT !!!**
- Add `"branch": "nextgen"` to `[proxy folder]/bin/config.json`, then restart proxy.
- If you want to go back to the live version, change branch to `"master"` and rename `[proxy folder]/mods/` to `[proxy folder]/bin/node_modules/`

# Changelog
## Major changes for end users
- Mods will be automatically migrated from `[proxy]/bin/node_modules/` to `[proxy]/mods/`.
  - Devs: this will break any attempt at `require()`ing other mods. Use `mod.game`/`mod.command`/`mod.require` instead!
- Proxy `config.json` will be automatically migrated from `[proxy]/bin/config.json` to `[proxy]/config.json`.
- Server list config files will be automatically migrated from `[proxy]/bin/lib/res/` to `[proxy]/bin/servers/`.
- Proxy core files will be automatically migrated from `[proxy]/bin/lib/` to `[proxy]/bin/`.
- Region improvements
  - Russian players will now be able to use proxy properly using both `www.tera-online.ru` and `launcher.tera-online.ru` (fixes proxy servers not appearing in list)
  - Removed the `KR-NAVER` region. If you're playing on Korean servers through through Naver, just change region to `KR` (it supports both Nexon and Naver logins now).


## General
- JS strict mode is now enforced globally. This means that you don't need to `"use strict"` your modules anymore, and it will give proxy a nice overall speed boost.
- Added `mod.require` with identical behavior to Pinkie's version.
  - Use this to require other mods, except for command/tera-game-state (use `mod.command` and `mod.game`!)
- `manifest.json` is now downloaded and stored in the mod's folder as well
- It is highly recommended that you set and maintain `"name"`, `"author"`, `"description"`, and optionally `"version"` (all strings, see example below) in `module.json` for each of your mods. This will facilitate making a module management GUI and advertise your module in an installation screen
- Proxy's working directory ('./') is now `[proxy]/` root folder instead of `[proxy]/bin/lib/`

## Added global proxy constants
There's now a new global object containing the following:
- `global.TeraProxy.DevMode`:
  - Can be set by adding `"devmode": true` to `[proxy]/config.json`
  - Modules can access this to determine whether or not to output additional (verbose) info, perform specialized stuff, etc.
  - Proxy core will use this in the future to annoy devs with deprecation warnings etc, but leave regular users in peace
- `global.TeraProxy.DiscordUrl`: invite link to my discord server
- `global.TeraProxy.SupportUrl`: link to help channel of my discord
  - If you don't have your own Discord server for support of your modules, feel free to add these to your error messages. Perhaps add your own Discord tag.

## Added `mod.info` object with the following attributes:
- `'type'`: `'regular'` (mod with its own folder) or `'standalone'` (single JS file)
- `'compatibility'`: `'compatible'` (auto update compatible) or `'legacy'` (old stuff)
- `'name'`: a unique identifier for the mod, e.g. `skill-prediction` (shortcut: `mod.name`)
  - Can be specified in `module.json` through `"name": "skill-prediction"` in the global object
  - If unspecified, the module's file name (standalone) or folder name (regular) is used instead
  - **Note: If multiple mods with identical names are installed, only one will be loaded!**
  - This prevents, for example, multiple installations of SP (skill-prediction and skill-prediction-master)
  - Similar to Pinkie's `mod.namespace`
- `'author'`: arbitrary string indicating module author(s) (from `module.json`, see example below)
- `'description'`: arbitrary string describing the module (from `module.json`, see example below)
- `'version'`: arbitrary string describing the module's current version (from `module.json`, see example below)
- `'donationUrl'`: arbitrary string indicating the module author's donation URL (from `module.json`, see example below)
- `'path'`: absolute path to the module's root folder (regular mods) or JS file (standalone mods)
- `'options'`: `module.json` options field (shortcut: `mod.options`)
- `'drmKey'`: `module.json` drm key
- `'supportUrl'`: `module.json` support url
- `'autoUpdateDisabled'`: `null` for legacy mods, `true` or `false` for compatible mods based on `module.json` settings
- `'packets'`: copy of `"def"` field in `manifest.json`
- `'dependencies'`: array of module names that this module requires to run (see below)
  - Note: this is extracted from only the keys of what's in `module.json`. The URLs are discarded
- `'conflicts'`: array of module names that must not be installed in order for this module to run

## Module management is now done by the ModuleManager class, which is separate from proxy.js and dispatch
- Accessible through `mod.manager`
- Interface:
  - `isInstalled(name)` checks if a module with `mod.name` === `name` is installed (regardless of whether it's loaded or not)
  - `getInfo(name)` returns the `mod.info` of the corresponding module
  - `isLoaded(name)` checks if the specified module is loaded
  - `get(name)` returns the `Module` instance (or `null` if not found).
    - **Note: Unlike the removed `dispatch.get`, this returns the module wrapper, not the module itself.**
    - **Use `get(name).instance` to access the module itself - however, `mod.require` is much more convenient for the same purpose**
  - `isCoreModule(name)` returns true for `'command'` and `'tera-game-state'`
  - `load(name)` loads the specified module (if not yet loaded) and returns its `Module` instance. **Use with caution, or even better - not at all!**
  - `unload(name)` unloads the specified module (if loaded). Returns true/false based on success. **Use with caution, or even better - not at all!**
  - `reload(name)` reloads the specified module if it supports hot-reloading (see below). Returns true/false based on success.

## Native support for module hot-reloading
- Needs to be explicitly enabled in `module.json` by setting `"reloadable": true` in the `"options": {}` field.
- If you need to transfer the internal state of your mod (for example info from your `S_LOGIN` hook which wouldn't be invoked without a relog):
  - Implement `saveState()` (returns an object with your mod's current state) and `loadState(state)` (said object, used to restore your mod's current state from `state`) functions in your mod.
  - Proxy will, in that order, call your mod's `saveState()`, `destructor()`, destroy your mod, delete your mod from require cache, reload your mod from disk, create a new instance (`constructor()`), and finally call `loadState(state)` with your saved state.

## Module management interface removed from `Dispatch`
- Deleted `mod.dispatch.isLoaded(name)` - use `mod.manager.isLoaded(name)` instead
- Deleted `mod.dispatch.get(name)` - use `mod.require.name`, `mod.require[name]`, or `mod.manager.get(name).instance` instead
- Deleted `mod.dispatch.load(name)` - use `mod.manager.load(name)` instead
- Deleted `mod.dispatch.unload(name)` - use `mod.manager.unload(name)` instead

## Improved error handling
- Better output for proxy self-update
  - Now also shows which files are updated when update log is enabled in `config.json`
  - Downloaded file hash verification to prevent update loops when GitHub takes its time, accompanied by proper error messages
- Def versions requested in `manifest.json` will now be checked _before_ loading the module. If any def is not supported, a list of incompatible ones will be printed and the mod will not be loaded.
- Errors in `dispatch` functions now throw an error instead of silently swallowing it or just printing a message
  - This also means that you can now handle failed hooks properly, like this:
  ```js
    // Hooking S_SOME_PACKET is optional
    try {
        mod.hook('S_SOME_PACKET', 1, event => {
            // Do stuff
        })
        
        // Hooking successful!
        this.SomeFeatureEnabled = true;
    } catch (_) {
        // Hooking failed - packet/def not supported, so disable optional feature.
        this.SomeFeatureEnabled = false;
    }
  ```
  - **Note about a rare edge case:** If you configure your module to be loaded before the protocol version is known (by default it's loaded afterwards), all hooks that you create before it becomes known will not support this feature.
- Simplified console formatting, started removing baldera-logger dependency

## Module Dependencies
Dependencies for modules can (and should!) now be specified in `module.json` and will be installed automatically if missing. `Please download dependency, library` - never again!
- Note that you do not need to specify dependencies on command and tera-game-state as these are core modules!
- Format is like this:
```json
{
    "disableAutoUpdate": false,
    "name": "skill-resets",
    "author": "Caali / eemj",
    "description": "Pops up an on-screen message whenever a skill cooldown is reset",
    "version": "1.0",
    "options": {
        "niceName": "SkillResets",
        "settingsVersion": 1,
        "settingsFile": "config.json",
        "settingsMigrator": "settings_migrator.js"
    },
    "servers": ["https://raw.githubusercontent.com/caali-hackerman/skill-resets/master/"],
    "dependencies": {
        "library": "https://raw.githubusercontent.com/Kaseaa/library/master/module.json"
    }
}
```

## Module Conflicts
Similar to dependencies, modules can also specify the names of other modules that must not be installed in order for them to run.
- Note that these are `mod.name`s, **not** folder names. So specifying, for example, `'skill-prediction'` here will block SP regardless of whether it's installed to `skill-prediction`, `sp`, `sp-master`, etc.
- Format is like this (`module.json`):
```js
{
    // ... snip ...
    "conflicts": ["skill-prediction", "ping-remover"]
}
```

## Improved logging
Added `mod.log(...)`, `mod.warn(...)`, and `mod.error(...)`
- Identical interface and behavior as `console.xxxx(...)`, but prefixes input with module name and `WARNING`/`ERROR` if applicable.
- Recommended to port all `console.xxxx` calls to `mod.xxxx` (simple find and replace) to be compatible with potential future enhancements to logging framework.
- This will also allow having per-connection logs instead of one global output, which will significantly improve multi-clienting.
