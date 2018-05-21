## Version 3.3

### New features

#### IPython console

* Add an option to use a tight layout with inline plots. It is
  present in `Preferences > IPython console > Graphics`.
* Add an option to turn on/off Jedi completions. It is present
  in `Preferences > IPython console > Advanced`.

#### Under the hood

* Add a new command line option called `--safe-mode` to start
  Spyder with a clean config directory.
* Remove support for PyQt 5.4 and older versions.
* Remove support for PyQt4.
* Remove support for Python 3.3.

----

## Version 4.0dev

### New features

#### Main Window

* Create a separate window when undocking all plugins.
* Add translations for Simplified Chinese and German.

#### Editor
* Add code folding functionality.
* Add indentation guidelines. They can be activated in the
  `Source` menu.
* Add a panel to show the current class and method/function
  where the cursor is placed. This is inspired by a similar
  functionality present in Microsoft Visual Studio. It can be
  activated in the `Source` menu.
* Allow setting several column edge lines in
  `Preferences > Editor > Display > Show vertical lines`.
* Add `Ctrl+Alt+Shift+,` and `Ctrl+Alt+Shift+.` to go the
  previous/next warning or error, respectively.
* Allow to scroll past the end of the file. This can be
  activated in
  `Preferences > Editor > Display > Scroll past the end`.
* Comment lines taking into account code indentation and pep8.
* Add an option to convert end-of-line characters on save.
* Add `Ctrl+{` and `Ctrl+_` for vertical and horizontal split
  of panels, respectively.
* Add `Alt+Shift+W` to close the current split panel.

#### Variable Explorer

* Add multi-index display support to the Dataframe viewer.
* Add support for all Pandas indexes.
* Add support for sets.

#### File Explorer

* Add `Open With OS` context menu action to all files, to open
  them with the program associated by the operating system.
* Add multi-select functionality (`Ctrl/Shift+click`).

#### Outline Explorer

* Show cells grouped in sections. Level 1 cells are defined by
  `#%%` (as before), level 2 cells by `#%%%`, level 3 cells by
  `#%%%%` and so on. By following this new syntax, all level
  n+1 cells will be shown inside level n cells in the outline
  tree.

#### API Changes

##### Major changes
* Create the `spyder.api` module to expose a public API for external
  plugins.

##### Minor changes
* Remove the `SpyderPluginMixin` class. Its contents were added to
  `BasePluginWidget` (in `plugins/base.py`) and `PluginWidget` (in
  `api/plugins.py`).
* Move `SpyderDockWidget` to `widgets/dock.py`.