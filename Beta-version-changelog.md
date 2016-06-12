## Version 3.0dev

### New features

#### Main Window

* The *Object Inspector* pane was renamed to *Help*.
* Add a new icon theme based on FontAwesome.
* Add *Introduction* and *New Features* interactive tutorials (under the `Help` menu).
* Add new default layouts (Horizontal, Vertical, Matlab and Rstudio), and also the
  possibility to name custom layouts.
* Panes that are tabbed next to each other can now be rearranged by dragging and
  dropping their tabs.
* Check for Spyder updates at startup, and also if you go to the menu entry
  `Help > Check for updates`.
* Add the shortcut `Shift+Alt+R` to restart the application.
* Add an option to warn when exiting the application, under
  `Preferences > General > Interface > Prompt when exiting`.
* Add Portuguese and Russian translations.
* Remove light mode

#### Settings
* Keyboard shortcuts can now be entered in an easier and more intuitive way.
* Add a menu entry to reset to default settings, under
  `Tools > Reset Spyder to factory defaults`.
* The language used in the main interface can now be changed. The option to
  do it is present in `General > Advanced Settings`.
* `Syntax coloring` now has a preview of the selected theme and it's able to
  change the current theme for all plugins.
* Plain and Rich text fonts for all plugins are now changed in
  `General > Appearance`.

#### Editor
* Add highlighting and code completion to all file types supported by Pygments
  (a syntax highlighting library)
* Use `Ctrl+M` and `Ctrl+Alt+M` to visually create matrices and vectors. It also
  works on the Python and IPython consoles.
* Add a new file switcher inspired by the Sublime Text one, which can be called
  with the `Ctrl+P` shortcut. It can also be used to look for classes, functions
  and methods inside a file, using the `@my_function` syntax.

#### IPython console
* Drop support for IPython 3.0 and older versions.
* Support the new `qtconsole` package instead. 

#### Debugging
* Enter debugging mode if running a file generates errors. This is not activated
  by default.

#### Profiler
* Add the ability to save and restore profiler data to compare speed improvements.

#### Working directory toolbar
* Get directory completions by pressing the `Tab` key twice on it

#### API Changes
* `spyderplugins` has been removed and its plugins have been assigned to different
  different directories (`spyder_profiler`, `spyder_breakpoints`, etc).
* `spyderlib.widgets.dicteditor.DictEditor` has been renamed to
  `spyderlib.widgets.variableexplorer.collectionseditor.CollectionsEditor`
* `spyderlib/widgets/dicteditorutils.py` has been renamed to
  `spyderlib/widgets/variableexplorer/utils.py`
* `spyderlib/widgets/externalshell/namespacebrowser.py` has been moved to
  `spyderlib/widgets/variableexplorer`
* `spyderlib/widgets/externalshell/syntaxhighlighters.py` has been moved to
  `spyderlib/utils/`
* Variable Explorer editor widgets were moved from `spyderlib.widgets`
  to `spyderlib.widgets.variableexplorer`:
    * `spyderlib.widgets.variableexplorer.arrayeditor`
    * `spyderlib.widgets.variableexplorer.collectionseditor`
    * `spyderlib.widgets.variableexplorer.objecteditor`
    * `spyderlib.widgets.variableexplorer.texteditor`
    * `spyderlib.widgets.variableexplorer.dataframeeditor`
* Modules used for configuration options (e.g. `spyderlib.config` and
  `spyderlib.baseconfig`) were moved to a new namespace:
  `spyderlib.config`
* Modules and files related to the application have been moved to
  `spyderlib.app` 
* `spyderlib/plugins/inspector.py` was renamed to
  `spyderlib/plugins/help.py`
* `spyderlib/utils/inspector` was renamed to `spyderlib/utils/help`
* `spyderlib.qt` was removed.

#### Under the hood
* Drop support for Python 2.6 and 3.2.
* Support PyQt5.
* Drop official support for PySide. Support for it will have to come from the community.
* Move our settings directory to `~/.spyder{-py3}`. Previous location was `~/.spyder2{-py3}`
* Use the new (pythonic) style for signals and slots.
* Start testing Spyder with the help of Travis and AppVeyor.
* Reorganize the code in several places (See Issue #1320).
* Code completions and help retrieval on the Editor are done asynchronously using a
  client/server architecture based on PyZMQ.
* Spyder now uses the `qtpy` package to be able to work with PyQt4 and PyQt5.