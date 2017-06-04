## Version 3.2dev

#### Main Window
* Add a dialog to quickly view all keyboard shortcuts defined in Spyder.
  It can be accessed in the `Help > Shortcuts Summary` menu or using
  the `Meta+F1` shortcut.
* Add an option to set a custom screen resolution scale factor. This option
  is available in `Preferences > Appearance > Screen resolution`.
* Prevent assignment of `Shift+<single key>` shortcuts because they can't be
  used by Qt applications unless they are hard-coded in the application
  itself.

#### Python Console
* Remove it for all operating systems. For an explanation, please see
  [this](https://github.com/spyder-ide/spyder/issues/4524).

#### Editor
* Add the ability to reorganize tabs by drag and drop.
* Add `Ctrl+Up` and `Ctrl+Down` shortcuts to move to the next/previous
  cell, respectively.
* Add `Alt+Enter` shortcut to re-run the last cell.
* Add support to run Cython files from the Editor (i.e. by simply
  pressing `F5`).
* Add syntax highlighting support for Markdown files.
* Add a tab switcher dialog to navigate files in most recently used
  order. This dialog is activated with `Ctrl+Tab` and
  `Ctrl+Shift+Tab` to go in forward or backward order, respectively.
* Make `Shift+Enter` search text backwards.
* Add `Shift+Del` shortcut to delete lines.
* Add a *Save copy as* action.
* Add an option to show the selected file in the operating system
  file explorer.
* Use `pycodestyle` package instead of `pep8` to do style analysis.

#### IPython Console
* Several improvements to its debugger:
  - Restore the ability to inspect variables using the Variable
    Explorer.
  - Make plotting work with a new `%plot` magic, but only using
    the `inline` backend (e.g. `%plot plt.plot(range(10))`).
  - Add history browsing with the Up and Down arrow keys.
  - Make the *Clear console* and *Reset* keyboard shortcuts to work.
  - Show plots from the Variable Explorer.
  - Change the current working directory using the Working Directory toolbar.
  - Use `Ctrl+Shift+C` to copy text.
* Automatically load the Cython extension if Cython is installed.

#### Find in Files

* Add options to search on the current file, project or path.
* Search path now refers to the path shown in the Working directory
  toolbar.
* Display results as search takes place.
* Allow to order results alphabetically.
* Add a spinner as indicator of a search in progress.
* Simplify visualization of results.
* Remove previous search results when a new search takes place.
* Improve file and string encoding to bypass and correct errors
  associated with codification.
* Inform users if the search regexp patterns are incorrect.
* Remove unused search options.
* Omit binary files.

#### File Explorer

* Add an option to show the selected file in the operating system
  file explorer.


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