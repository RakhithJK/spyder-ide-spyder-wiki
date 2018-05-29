## Version 3.3

### New features

#### IPython console

* Add an option to use a tight layout with inline plots.
  Activate it under `Preferences > IPython console > Graphics`.
* Add an option to turn on/off Jedi completions.
  Activate it under `Preferences > IPython console > Advanced`.

#### Variable Explorer
* Change button names in its Dataframe, Numpy array, etc viewers
  to better express what operation each one performs.

#### Under the hood

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
* Add indentation guides. 
  They can be activated under the `Source` menu.
* Add a panel to show the current class and method/function
  where the cursor is placed, inspired by similar 
  functionality present in Microsoft Visual Studio. 
  It can activated under the `Source` menu.
* Allow setting multiple line length indicators under
  `Preferences > Editor > Display > Show vertical lines`.
* Add `Ctrl+Alt+Shift+,` and `Ctrl+Alt+Shift+.` shortcuts 
  to go to the previous/next warning and error, respectively.
* Allow scrolling past the end of the file. 
  This can activated in
  `Preferences > Editor > Display > Scroll past the end`.
* Add the ability to consider code indentation and PEP 8 
  when adding and removing comment levels.
* Add an option to convert end-of-line characters on save.
* Add `Ctrl+{` and `Ctrl+_` shortcuts to split panels 
  vertically and horizontally, respectively.
* Add `Alt+Shift+W` shortcut to close the current split panel.

#### Variable Explorer

* Add MultiIndex display support to the DataFrame viewer.
* Add support for all Pandas indexes.
* Add support for sets.

#### File Explorer

* Add `Open With OS` context menu action to all files, 
  to open them with the user's Operating System
  default program associated with their file type.
* Add multi-select functionality (`Ctrl/Shift+click`).

#### Outline Explorer

* Show cells grouped in sections. Level 1 cells are defined by
  `#%%` (as before), level 2 cells by `#%%%`, level 3 cells by
  `#%%%%` and so on. If using this new syntax, all  n+1 cells
  will be conveniently grouped under top-level cells in the 
  outline tree.

#### API Changes

##### Major changes
* Create the `spyder.api` module to expose a public API
  for external plugins.

##### Minor changes
* Remove the `SpyderPluginMixin` class. 
  Its contents were added to `BasePluginWidget` (in `plugins/base.py`)
  and `PluginWidget` (in `api/plugins.py`).
* Move `SpyderDockWidget` to `widgets/dock.py`.