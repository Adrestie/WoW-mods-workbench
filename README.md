# The workbench

A component shared by the [WoW-mods](https://github.com/Adrestie/WoW-mods) modules: one object in the world (game object 810000), one window, and any number of modules bringing their recipes to it.

## Key features

- One crafting window for every module: three slots, the result, a "Craft" button.
- The bags' matching items listed under a slot, sorted by type, quality and name.
- A preview of the result before crafting, and the recipes listed in the window.
- Texts in English, French, German, Spanish and Russian.
- Used by [mod-spheregrid](https://github.com/Adrestie/mod-spheregrid) and [mod-stellar-tarot](https://github.com/Adrestie/mod-stellar-tarot).

## Dependencies

| Dependency | For |
|---|---|
| [mod-ale](https://github.com/azerothcore/mod-ale) | runs the bench on the server |
| [AIO](https://github.com/Rochet2/AIO) | the window: `AIO_Server` in `lua_scripts`, and the `AIO_Client` addon on every client |

## How to install

Nothing to install on its own: every module that uses the bench carries a copy as `data/lua/Workbench/`, and [WoW-mods-installer](https://github.com/Adrestie/WoW-mods-installer) places it in `lua_scripts/Workbench/` when it installs that module.

In a module's repository, the folder comes through `git subtree`, and the module registers its recipes with `Workbench.Register({...})` from its own Lua (see `Workbench.ext`).

## How to update

Update a module that uses the bench with the installer (**Update**): the installed bench is replaced when the module's copy is newer (`VERSION`).

In a module's repository: `git subtree pull --prefix=data/lua/Workbench https://github.com/Adrestie/WoW-mods-workbench.git main --squash`.

## How to uninstall

Remove the modules that use it with the installer (**Remove**): the last one to go removes the bench and its object.
