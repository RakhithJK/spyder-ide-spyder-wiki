## Version 2.4dev

### New features since v2.3

* Editor
  * Add highlighting to all file types supported by Pygments (a syntax highlighting library)

* Debugging
  * Integrate post mortem debugging when running a file

* Profiler
  * Add the ability to save and restore profiler data to compare speed improvements

* Main Window
  * Add *Introduction* and *New Features* interactive tutorials
  * Add new default layouts (Horizontal, Vertical, Matlab and Rstudio), and also the possibility to name custom layouts.
  * Add an option to warn when exiting the application, under `Preferences > General > Interface > Prompt when exiting`

* Under the hood
  * Support PyQt5
  * Use the new (pythonic) style for signals and slots
  * Use PyQt4 API #2 by default (API #1 is now unsupported)