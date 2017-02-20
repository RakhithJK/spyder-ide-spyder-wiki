## Version 3.2dev

#### Editor
* Add the ability to reorganize tabs by drag and drop

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