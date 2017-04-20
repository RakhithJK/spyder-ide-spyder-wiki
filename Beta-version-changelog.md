## Version 3.2dev

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

#### IPython Console
* Automatically load the Cython extension if Cython is installed.

----


## Version 4.0dev

### New features

#### Editor
* Add code folding functionality.
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