## Version 3.2.7

#### Main Window

* Improve the interface to report errors to Github.

#### Variable Explorer

* Enable the display of many more Numpy array types.

#### Editor

* Copy text from the search field to the replace one
  after pressing `Tab`.

#### IPython console

* Make `%edit foo.py` open `foo.py` in our Editor on
  Windows.

### Find in Files

* Remove items from the `Search in` list when hovering
  over them and pressing `Del`.
* Add a `Clear this list` option below `Select other
  directory`.

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

#### API Changes

##### Major changes
* Create the `spyder.api` module to expose a public API for external
  plugins.

##### Minor changes
* Remove the `SpyderPluginMixin` class. Its contents were added to
  `BasePluginWidget` (in `plugins/base.py`) and `PluginWidget` (in
  `api/plugins.py`).
* Move `SpyderDockWidget` to `widgets/dock.py`.