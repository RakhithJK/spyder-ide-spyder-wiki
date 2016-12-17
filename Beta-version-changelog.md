## Version 3.1dev

### New features

#### Editor
* Add the Solarized Light and Dark color schemes.
* Add support for greedy regular expressions in the find/replace widget
  (only available under PyQt5).
* Improve the use of tabs instead of spaces for indentation.
* Add `Ctrl+Shift+T` shortcut to reopen the last closed file.
* Show completions for Numpy and Matplotlib compiled objects (e.g.
  `np.array` and `plt.figure`)

#### Variable Explorer
* Add support for the most important numeric types of Numpy (32 and 64
  bits int, float and complex numbers).
* Save format for floats in DataFrame editor.
* Make the index column of DataFrame editor always visible when scrolling
  to right and left.

#### IPython Console
* Be able to load kernel json files anywhere in the file system when
  connecting to external kernels.

#### Settings
* Make all keyboard shortcuts configurable

#### Under the hood
* Add the chardet and numpydoc libraries as new dependencies.
* Add the `--project <path-to-dir>` command line option to load
  projects at startup.


----


## Version 4.0dev

### New features

#### Editor
* Allow setting several column edge lines in
  `Preferences > Editor > Display > Show vertical lines after`  

#### Python Console
* Disconnect it from the Variable Explorer

#### API Changes

##### Major changes
* Create the module `spyder.api` to expose a public API for external
  plugins.

##### Minor changes
* Remove the `SpyderPluginMixin` class. Its contents were added to
  `BasePluginWidget` (in `plugins/base.py`) and `PluginWidget` (in
  `api/plugins.py`).
* Move `SpyderDockWidget` to `widgets/dock.py`.