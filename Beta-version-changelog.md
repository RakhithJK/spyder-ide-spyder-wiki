## Version 4.0dev

### New features

#### Main Window

* Add translations for Simplified Chinese and German.

#### Editor
* Add code folding functionality.
* Add indentation guidelines. They can activated in the Source
  menu.
* Add a new panel to show the current class and method/function
  where the cursor is placed. This is inspired by a similar
  functionality present in Microsoft Visual Studio. It can be
  activated in the Source menu.
* Allow setting several column edge lines in
  `Preferences > Editor > Display > Show vertical lines`.
* Add `Ctrl+Alt+Shift+,` and `Ctrl+Alt+Shift+.` to go the
  previous/next warning or error, respectively.

#### Variable Explorer

* Add support for all Pandas indexes.

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