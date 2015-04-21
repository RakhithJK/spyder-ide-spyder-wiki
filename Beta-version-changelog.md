## Version 3.0dev

### New features since v2.3

* Drop support for Python 3.2

* Editor
  * Add highlighting to all file types supported by Pygments (a syntax highlighting library)
  * Use `Ctrl+*` and `Shift+Ctrl+*` to visually create matrices and vectors. It also works on the Python and IPython consoles.

* IPython console
  * Drop support for IPython versions less than 3.0

* Debugging
  * Integrate post mortem debugging when running a file

* Profiler
  * Add the ability to save and restore profiler data to compare speed improvements

* Main Window
  * Add *Introduction* and *New Features* interactive tutorials
  * Add new default layouts (Horizontal, Vertical, Matlab and Rstudio), and also the possibility to name custom layouts.
  * Add the shortcut `Shift+Alt+R` to restart the application.
  * Add an option to warn when exiting the application, under `Preferences > General > Interface > Prompt when exiting`

* Add Brazilian Portuguese translation

* Under the hood
  * Support PyQt5
  * Move our settings directory to `~/.spyder{-py3}`
  * Use the new (pythonic) style for signals and slots
  * Use PyQt4 API #2 by default (API #1 is not supported anymore)
  * Start testing Spyder with the help of Travis CI