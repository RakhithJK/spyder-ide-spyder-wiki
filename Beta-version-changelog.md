## Version 3.2dev

#### Main Window
* Add a dialog to quickly view all keyboard shortcuts defined in Spyder.
  It can be accessed in the `Help > Shortcuts Summary` menu or using
  the `Meta+F1` shortcut.

#### Editor
* Add the ability to reorganize tabs by drag and drop.
* Use `pycodestyle` package instead of `pep8` to do style analysis.
* Add `Alt+Enter` as a shortcut to re-run the last cell.
* Add support to run Cython files from the Editor (i.e. by simply
  pressing `F5`).
* Add syntax highlighting support for Markdown files.
* Add a tab switcher dialog to navigate files in most recently used
  order. This dialog is activated with `Ctrl+Tab` and
  `Ctrl+Shift+Tab` to go in forward or backward order, respectively.
* Add `Ctrl+Up` and `Ctrl+Down` shortcuts to move to the next/previous
  cell, respectively.

#### Find in files

* Add options to search on the current file, project or current path.
* Simplify visualization of results.
* Display results as search takes place.
* Add a spinner as indicator of a search in progress.
* Search path now refers to the path shown in the Working directory
  toolbar.
* Remove previous search results when a new search takes place.
* Improve file and string encoding to bypass and correct errors
  associated with codification.
* Inform users if the search regexp patterns are incorrect.
* Remove unused search options.
* Omit binary files.
* Allow to order results alphabetically.


#### IPython Console
* Automatically load the Cython extension if Cython is installed.

----


## Version 4.0dev

### New features

#### Editor
* Add code folding functionality.
* Add a new panel to show the current class and method/function
  where the cursor is placed. This is inspired by a similar
  functionality present in Microsoft Visual Studio. 
* Allow setting several column edge lines in
  `Preferences > Editor > Display > Show vertical lines`  

#### Python Console
* Disconnect it from the Variable Explorer

#### API Changes

##### Major changes
* Create the `spyder.api` module to expose a public API for external
  plugins.

##### Minor changes
* Remove the `SpyderPluginMixin` class. Its contents were added to
  `BasePluginWidget` (in `plugins/base.py`) and `PluginWidget` (in
  `api/plugins.py`).
* Move `SpyderDockWidget` to `widgets/dock.py`.