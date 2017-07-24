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
  functionality present in Microsoft Visual Studio. 
* Allow setting several column edge lines in
  `Preferences > Editor > Display > Show vertical lines`.

#### API Changes

##### Major changes
* Create the `spyder.api` module to expose a public API for external
  plugins.

##### Minor changes
* Remove the `SpyderPluginMixin` class. Its contents were added to
  `BasePluginWidget` (in `plugins/base.py`) and `PluginWidget` (in
  `api/plugins.py`).
* Move `SpyderDockWidget` to `widgets/dock.py`.