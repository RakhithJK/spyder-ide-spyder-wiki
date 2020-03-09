This section aims to give an introduction into Spyder internals.

**Note: This is a work in progress!**

# Directory Structure

The following tree represents the current structure of Spyder master repo. The branches here represent only folders, more specifics and explanations will be given below. The most important directories for a developer are probably `spyderlib/plugins` and `spyderlib/widgets`.


:open_file_folder: [spyder-ide/spyder.git](https://github.com/spyder-ide/spyder)  <br>
├── [binder](#binder)  <br>
├── [continuous_integration](#continuous_integration) ··············· *Scripts for continuous integration*  <br>
├── [external-deps/spyder-kernels](#spyder-kernels)  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [spyder-kernels](#spyder-kernels) ······························ *Jupyter kernels for the Spyder console*  <br>
├── [img_src](#img_src) ····························· *Images and other artwork*  <br>
├── [requirements](#requirements) ····················· *version requirements of components/libraries specified*  <br>
├── [rope_profiling](#rope_profiling)  <br>
├── [scripts](#scripts)  <br>
├── [spyder](#spyder) ··························· *Main library*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [api](#api) ······························ *All the component API's*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [app](#app) ······························ *Entry point for (re)starting*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [config](#config) ·························· *User configuration*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [fonts](#fonts) ···························· *Spline Font Database for Spyder font*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [images](#images) ······················· *Images for various components*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [locale](#locale) ························· *Translations*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [plugins](#plugins) ······················· *Main components of Spyder*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [preferences](#preferences) ······················· *Preference dialogue with user for Spyder*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [tests](#tests)  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [utils](#utils) ····························· *Utility functions*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [widgets](#widgets) ······················ *GUI elements*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [windows](#windows) ····················· *ICO format images of spyder for Windows*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;└── [workers](#workers) ······················· *checks for new releases*  <br>
├── [tools](#tools) ················· *scripts for external tools*  <br>

## binder
[Binder](https://mybinder.org/) files for setting up environment.

## continuous_integration
After every commit, Spyder is built automatically and the tests are run. The required scripts reside in this directory. We use two platforms: [AppVeyor](https://ci.appveyor.com/project/ccordoba12/spyder) (for Windows) and [Travis](https://travis-ci.org/spyder-ide/spyder/) (for Linux).


## spyder-kernels
Package that provides Jupyter kernels for use with the consoles of Spyder, the Scientific Python Development Environment.

## requirements
Contains text files specifying required versions of components/libraries for building the environment.

## img_src
This folder holds the editable and rendered versions of images and art for the Spyder project.

Included files: Official icons, main logo, and some screenshots.

## spyder
This is the actual main module of Spyder.

Earlier this folder was originally named `spyderlib` due to the existence of another project named "spyder". However, now it has been renamed to `spyder`  

### api
This folder contains API's for editor, panel, manager, plugins etc.

### app
This folder contains the entry point for the Spyder application and also the logic for restarting the application.

### config
This folder contains files to do with handling the user configuration. The configuration is divided in sections which correspond to the plugins. Read the note at the bottom of `main.py` if you want to change, add or remove a configuration setting. 

### fonts
Contains Spline Font Database for Spyder font. 

### images
This folder contains all the images used in components like editor, editor and GUI in general.

### locale 
The translations of the interface for Spyder are stored in this folder. Currently Spyder has translations available for Brazilian Portuguese (pt_BR), Chinese (zh_CN), French (fr), German (de), Hungarian (hu), Japenese (ja), Spanish (es), Polish (pl), Russian (ru).

If you would like to have Spyder translated to a new language please drop us a line on the [public chat](https://gitter.im/spyder-ide/public).

### plugins
The code for Spyder is divided in several parts, called plugins, which reside in this folder. A plugin consists of a widget with some extra code to embed the widget within the Spyder application: entries in the configuration object, shortcut key bindings, toolbar icons, menu items, and collaboration with other plugins using the Qt signal/slot mechanism. The widget may be a standard Qt widget or one of the widgets defined in the [widgets](#widgets) folder. The main plugin class inherits from both its main widget and `SpyderPluginMixin`. This can be achieved by having the main plugin class inherit from `SpyderPluginWidget`, which in turn inherits from `QWidget` and `SpyderPluginMixin`.

The following plugins are defined in Python files with the same name:
- `Console` (the internal console)
- `Editor` (the code editor)
- `Explorer` (the file and directory explorer)
- `FindInFiles` (the "find in files" tool)
- `Help` (the object inspector, for viewing docstrings)
- `History` (the history log)
- `IPythonConsole` (IPython console)
- `OnlineHelp` (uses pydoc to generate online help from docstrings)
- `OutlineExplorer` (displays the outline of files)
- `Projects` (for browsing the current project)
- `VariableExplorer` (for browsing and editing variables)
- `WorkingDirectory` (the widget in the toolbar which displays the working directory)

Also contains external plugins such as profiler, pylint, io_dcm and io_hdf5.

### preferences
This folder contains code files responsible for dialogue with user to set preferences/configuration of the environment.

### utils
This is the location of many common use functions or helpers that make Spyder work and developed in a more consistent way.

### widgets
These are widgets (Graphical User Interface elements) that are used in Spyder. It should be possible to use these widgets outside Spyder. Ideally, each file when run will display the corresponding widget. Widgets can be embedded in plugins defined in the [plugins](#plugins) folder, which are responsible for connecting the widgets together into a coherent application (namely Spyder).


### windows
Contains ICO format images of spyder for Windows.

### workers
Worker that checks for releases using either the Anaconda default channels or the Github Releases page without blocking the Spyder user interface, in case of connection issues.