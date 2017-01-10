## Version 3.1dev

### New features

#### Editor
* Add the Solarized Light and Dark color schemes.
* Add support for greedy regular expressions in the find/replace widget
  (only available with PyQt5).
* Improve the use of tabs instead of spaces for indentation.
* Add `Ctrl+Shift+T` shortcut to reopen the last closed file.
* Show completions for Numpy and Matplotlib compiled objects (e.g.
  `np.array` and `plt.figure`)
* Disambiguate tabs in case users open several files with the same
  name.
* Add the shortcut `Ctrl+Alt+P` to open a switcher to select among
  the symbols (functions, methods or classes) present in a file.
  Also add an entry in the `File` menu and toolbar button to show
  this switcher. 

#### Variable Explorer
* Add support for the most important numeric types of Numpy (32 and 64
  bits int, float and complex numbers).
* Save format for floats in DataFrame editor.
* Make the index column of DataFrame editor always visible when scrolling
  to right and left.
* Add support for Pandas DatetimeIndex objects.
* Show empty Numpy arrays.

#### IPython Console
* Be able to load kernel json files anywhere in the file system when
  connecting to external kernels.
* Add an option (under `Preferences > Run` and `Run > Configure`) to
  clear all variables present in a console before running a file (it
  runs `%reset -f` in the associated kernel).

#### Profiler
* Show time units (in seconds) spent by each function or method.

#### Settings
* Make all keyboard shortcuts configurable

#### Under the hood
* Add the `--project <path-to-dir>` command line option to load
  projects at startup.
* Add the chardet and numpydoc libraries as new dependencies.


----


## Version 4.0dev

### New features

#### Editor
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