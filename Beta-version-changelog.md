## Version 3.0dev

### New features

#### Main Window
  
* Add a new icon theme based on FontAwesome.
* Add *Introduction* and *New Features* interactive tutorials.
* Add new default layouts (Horizontal, Vertical, Matlab and Rstudio), and also the possibility to name custom layouts.
* Panes that are tabbed next to each other can now be rearranged by drag and drop their tabs.
* Check for Spyder updates at startup, and also if you go to the menu entry `Help > Check for updates`.
* Add the shortcut `Shift+Alt+R` to restart the application.
* Add an option to warn when exiting the application, under `Preferences > General > Interface > Prompt when exiting`.
* Add Portuguese translation.

#### Settings
* Keyboard shortcuts can now be entered in an easier and more intuitive way.
* Add a menu entry to reset to default settings, under `Tools > Reset Spyder to factory defaults`.
* The language used in the main interface can now be changed. The option to do it is present in `General > Interface > Language`.

#### Editor
* Add highlighting to all file types supported by Pygments (a syntax highlighting library)
* Use `Ctrl+*` and `Shift+Ctrl+*` to visually create matrices and vectors. It also works on the Python and IPython consoles.
* Add a new file switcher inspired by the Sublime Text one, which can be called with the `Ctrl+P` shortcut. It can also be used to look for classes/functions/methods inside a file, using the `@my_function` syntax.

#### IPython console
* Drop support for IPython versions less than 3.0.

#### Debugging
* Integrate post mortem debugging when running a file.

#### Profiler
* Add the ability to save and restore profiler data to compare speed improvements

#### API Changes
* `spyderlib.dicteditor.DictEditor` has been renamed to `spyderlib.widgets.variableexplorer.collectionseditor.CollectionsEditor`
* Variable Explorer editor widgets were moved from `spyderlib.widgets`
to `spyderlib.widgets.variableexplorer`:
    * `spyderlib.widgets.variableexplorer.arrayeditor`
    * `spyderlib.widgets.variableexplorer.collectionseditor`
    * `spyderlib.widgets.variableexplorer.objecteditor`
    * `spyderlib.widgets.variableexplorer.texteditor`
    * `spyderlib.widgets.variableexplorer.dataframeeditor`
* Modules used for configuration options (e.g. `spyderlib.config` and
`spyderlib.baseconfig`) were moved to a new namespace: `spyderlib.config`

#### Under the hood
* Drop support for Python 2.6 and 3.2.
* Support PyQt5.
* Move our settings directory to `~/.spyder{-py3}`. Previous location was `~/.spyder2{-py3}`
* Use the new (pythonic) style for signals and slots.
* Start testing Spyder with the help of Travis CI.
* Reorganize the code in several places (See Issue #1320).