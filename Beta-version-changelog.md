## Version 3.2dev

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