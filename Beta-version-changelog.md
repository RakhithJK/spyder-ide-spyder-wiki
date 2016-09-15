## Version 3.0dev

### New features

#### Main Window

* The *Object Inspector* pane was renamed to *Help*.
* Add a new icon theme based on FontAwesome.
* Add an *Introduction* interactive tutorial (under the `Help` menu).
* Add new default layouts (Horizontal, Vertical, Matlab and Rstudio), and also the
  possibility to name custom layouts.
* Panes that are tabbed next to each other can now be rearranged by dragging and
  dropping their tabs.
* Check for Spyder updates at startup, and also if you go to the menu entry
  `Help > Check for updates`.
* Add the shortcut `Shift+Alt+R` to restart the application.
* Add an option to warn when exiting the application, under
  `Preferences > General > Interface > Prompt when exiting`.
* Add Portuguese, Russian and Japanese translations.
* Remove light mode

#### Editor
* Add highlighting and code completion to all file types supported by Pygments
  (a syntax highlighting library)
* Use `Ctrl+M` and `Ctrl+Alt+M` to visually create matrices and vectors. It also
  works on the Python and IPython consoles.
* Add a new file switcher inspired by the Sublime Text one, which can be called
  with the `Ctrl+P` shortcut. It can also be used to look for classes, functions
  and methods inside a file, using the `@my_function` syntax.

#### Projects:
* A new menu entry called *Projects* was added to the main window with all
  actions related to projects.
* A project now saves the state of open files in the Editor, so that people can
  easily work on different coding efforts at the same time.
* The project's path is added to `PYTHONPATH`, so that Python packages
  developed as part of a project can be easily imported in Spyder consoles.
* The project explorer now shows a file tree view of the current project, as
  other editors and IDEs do (e.g. Sublime Text and VSCode).
* Projects are completely optional and not imposed on users, i.e. users can work
  without creating any project.

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
* Add a new entry called `Python interpreter` to allow people to select the
  interpreter used for all Python and IPython consoles (this was before in
  `Console > Advanced settings`).
* Rename the `Console` entry to `Python console`.

#### IPython console
* Drop support for IPython 3.0 and older versions.
* Support the new `qtconsole` package instead. 
* Communicate directly with IPython kernels instead of doing it through the
  Python  console.

#### Debugging
* Enter debugging mode if running a file generates errors. This is not activated
  by default but you can do it by going to `Run > Configure > General settings`.

#### Profiler
* Add the ability to save and restore profiler data to compare speed improvements.

#### Working directory toolbar
* Get directory completions by pressing the `Tab` key twice on it.

#### API Changes

##### Major changes
* The `spyderlib` module was renamed to `spyder`
* `spyderplugins` has been removed and its plugins have been assigned to different
  different modules (`spyder_profiler`, `spyder_breakpoints`, etc) still
  distributed with the Spyder package.

##### Minor changes
* `spyderlib.widgets.dicteditor.DictEditor` has been renamed to
  `spyder.widgets.variableexplorer.collectionseditor.CollectionsEditor`.
* `spyderlib/widgets/dicteditorutils.py` has been renamed to
  `spyder/widgets/variableexplorer/utils.py`.
* `spyderlib/widgets/externalshell/namespacebrowser.py` has been moved to
  `spyder/widgets/variableexplorer`.
* `spyderlib/widgets/externalshell/syntaxhighlighters.py` has been moved to
  `spyder/utils/`.
* Variable Explorer editor widgets were moved from `spyderlib.widgets`
  to `spyder.widgets.variableexplorer`:
    * `spyder.widgets.variableexplorer.arrayeditor`
    * `spyder.widgets.variableexplorer.collectionseditor`
    * `spyder.widgets.variableexplorer.objecteditor`
    * `spyder.widgets.variableexplorer.texteditor`
    * `spyder.widgets.variableexplorer.dataframeeditor`
* Modules used for configuration options (e.g. `spyderlib.config`,
  `spyderlib.baseconfig`, etc) were moved to a new namespace called
  `spyder.config`.
* Modules and files related to the application have been moved to
  `spyder.app`.
* `spyderlib/plugins/projectexplorer.py` has been renamed to
  `spyder/plugins/projects.py`
* `spyderlib/widgets/projectexplorer.py` has been renamed to
  `spyder/widgets/projects/explorer.py`
* `spyderlib/plugins/inspector.py` was renamed to
  `spyder/plugins/help.py`.
* `spyderlib/utils/inspector` was renamed to `spyder/utils/help`.
* `spyderlib.qt` was removed.
* `spyderlib/widgets/ipython.py` was broken in several files inside
   `spyder/widgets/ipythonconsole`.
* `spyder/widgets/externalshell/{sitecustomize.py, osx_app_site.py}` were
  moved to `spyder/utils/site`
* `spyder/widgets/externalshell/start_ipython_kernel.py` was moved to
  `spyder/utils/ipython`

#### Under the hood
* Drop support for Python 2.6 and 3.2.
* Support PyQt5.
* Drop official support for PySide. Support for it will have to come from the community.
* Move our settings directory to `HOME/.spyder{-py3}`. Previous location was `HOME/.spyder2{-py3}`
  * On Linux we now follow the XDG specification to save our settings, i.e. they are saved in
    `~/.config/spyder{-py3}` or `$XDG_CONFIG_HOME/spyder{-py3}` if `$XDG_CONFIG_HOME` is
    defined.
* Use the new (pythonic) style for signals and slots.
* Test Spyder with the help of Travis and AppVeyor.
* Code completions and help retrieval on the Editor are done asynchronously using a
  client/server architecture based on PyZMQ.
* Spyder now uses the `qtpy` package to be able to work with PyQt4 and PyQt5 seamlessly.