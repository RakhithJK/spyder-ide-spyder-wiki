This section aims to give an introduction into Spyder internals.

**Note: This is a work in progress!**

# Directory Structure

The following tree represents the current structure of Spyder master repo. The branches here represent only folders, more specifics and explanations will be given below. The most important directories for a developer are probably `spyderlib/plugins` and `spyderlib/widgets`.


:open_file_folder: [spyder-ide/spyder.git](https://github.com/spyder-ide/spyder)  <br>
├── [app_example](#app_example)  <br>
├── [conda.recipe](#conda.recipe) ···················· *For creating conda package*  <br>
├── [continuous_integration](#continuous_integration) ··· *Scripts for continuous integration*  <br>
├── [doc](#doc) ····································· *Documentation*  <br>
├── [external-py2](#external-py2) ····················· *Copies of external libraries*  <br>
├── [external-py3](#external-py3) ····················· *Copies of external libraries*  <br>
├── [img_src](#img_src) ····························· *Images and other artwork*  <br>
├── [rope_profiling](#rope_profiling)  <br>
├── [scripts](#scripts)  <br>
├── [spyder_breakpoints](#spyder_xxx) ········ *External plugin*  <br>
├── [spyder_io_dcm](#spyder_xxx) ················ *External plugin*  <br>
├── [spyder_io_hdf5](#spyder_xxx) ················ *External plugin*  <br>
├── [spyderlib](#spyderlib) ··························· *Main library*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [app](#app) ······························ *Entry point for (re)starting*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [config](#config) ·························· *User configuration*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [defaults](#defaults) ······················ *For upgrading from pre-2.3 versions*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [fonts](#fonts) ···························· *TODO:*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [images](#images) ······················· *TODO:*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [locale](#locale) ························· *Translations*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [plugins](#plugins) ······················· *Main components of Spyder*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [utils](#utils) ····························· *Utility functions*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [widgets](#widgets) ······················ *GUI elements*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [externalshell](#externalshell) ······· *TODO:*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;└── [sourcecode](#sourcecode) ········· *Code editor widget, Syntax highlighting*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [windows](#windows) ····················· *TODO:*  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;└── [workers](#workers) ······················· *TODO:*  <br>
├── [spyder_profiler](#spyder_xxx) ················· *External plugin*  <br>
└── [spyder_pylint](#spyder_xxx) ···················· *External plugin*  <br>

## app_example
TODO:

## conda.recipe
This folder contains files necessary for building the conda package for installing Spyder. See [Conda build recipes](http://conda.pydata.org/docs/building/recipe.html) for more information.

## continuous_integration
After every commit, Spyder is built automatically and the tests are run. The required scripts reside in this directory. We use two platforms: [AppVeyor](https://ci.appveyor.com/project/ccordoba12/spyder) (for Windows) and [Travis](https://travis-ci.org/spyder-ide/spyder/) (for Linux).

## doc
As the name suggests this is the folder where the documentation of the project resides. 

The documentation is written in [reStructuredText](http://docutils.sourceforge.net/rst.html) (.rst) and is parsed using [Sphinx](http://sphinx-doc.org/).

The documentation is hosted in [Python Hosted](https://pythonhosted.org/spyder/).

## external-py2
Spyder makes use of external python libraries, such as [pyflakes](https://github.com/pyflakes/pyflakes/), [rope](http://rope.sourceforge.net/), [pep8](https://github.com/jcrocholl/pep8) and a modified version of the [conda_api](https://github.com/conda/conda-api). When Spyder runs from a Python 2 interpreter, the `external-py2` folder is added to the `PATH`. 

The modules saved here must be compatible with Python 2.

## external-py3
Spyder makes use of external python libraries, such as [pyflakes](https://github.com/pyflakes/pyflakes/), [rope](http://rope.sourceforge.net/), [pep8](https://github.com/jcrocholl/pep8) and a modified version of the [conda_api](https://github.com/conda/conda-api). When Spyder runs from a Python 3 interpreter, the `external-py3` folder is added to the `PATH`. 

The modules saved here must be compatible with Python 3.

**Note: Even if the same module works with both Python 2 and Python 3, it must be copied inside both `external-py2` and `external-py3` folders.**

## img_src
This folder holds the editable and rendered versions of images and art for the Spyder project.

Included files: Official icons, main logo, and some screenshots.

## rope_profiling
TODO:

## scripts
TODO:

## spyder_xxx
These are external plugins which are distributed with Spyder. External plugins are similar to normal [plugins](#plugins) but live outside the main spyderlib module. See [[User plugins]] and [[Writing plugins]] for more information from a user's and developer's perspective, respectively.

## spyderlib
This is the actual main module of Spyder.

The name `spyderlib` was originally chosen due to the existence of another project named "spyder." However, this folder is soon to be renamed to `spyder`.

### app
This contains the entry point for the Spyder application and also the logic for restarting the application.

### config
This folder contains files to do with handling the user configuration. The configuration is divided in sections which correspond to the plugins. In the rest of the code, the object containing the configuration data is called `CONF`. Read the note at the bottom of `main.py` if you want to change, add or remove a configuration setting. 

### defaults
The files present here are used to cleanly update user configuration options from Spyder versions previous to 2.3.

### fonts
TODO:

### images
TODO:

### locale 
The translations of the interface for Spyder are stored in this folder. Currently Spyder has translations available for Spanish (es), French (fr), Brazilian Portuguese (pt_BR) and Russian (ru).

If you would like to have Spyder translated to a new language please drop us a line on the [public chat](https://gitter.im/spyder-ide/public).

### plugins
The code for Spyder is divided in several parts, called plugins, which reside in this folder. A plugin consists of a widget with some extra code to embed the widget within the Spyder application: entries in the configuration object, shortcut key bindings, toolbar icons, menu items, and collaboration with other plugins using the Qt signal/slot mechanism. The widget may be a standard Qt widget or one of the widgets defined in the [widgets](#widgets) folder. The main plugin class inherits from both its main widget and `SpyderPluginMixin`. This can be achieved by having the main plugin class inherit from `SpyderPluginWidget`, which in turn inherits from `QWidget` and `SpyderPluginMixin`.

The following plugins are defined in Python files with the same name:
- `Console` (the internal console)
- `Editor` (the code editor)
- `Explorer` (the file and directory explorer)
- `ExternalConsole` (external console; to be refactored with IPythonConsole at time of writing)
- `FindInFiles` (the "find in files" tool)
- `Help` (the object inspector, for viewing docstrings)
- `HistoryLog` (the history log)
- `IPythonConsole` (IPython console; to be refactored with ExternalConsole at time of writing)
- `OnlineHelp` (uses pydoc to generate online help from docstrings)
- `OutlineExplorer` (displays the outline of files)
- `ProjectExplorer` (for browsing the current project)
- `VariableExplorer` (for browsing and editing variables)
- `WorkingDirectory` (the widget in the toolbar which displays the working directory)

### utils
This is the location of many common use functions or helpers that make Spyder work and developed in a more consistent way.

### widgets
These are widgets (Graphical User Interface elements) that are used in Spyder. It should be possible to use these widgets outside Spyder. Ideally, each file when run will display the corresponding widget. Widgets can be embedded in plugins defined in the [plugins](#plugins) folder, which are responsible for connecting the widgets together into a coherent application (namely Spyder).

#### externalshell
TODO:

#### sourcecode
TODO:

### windows
TODO:

### workers
TODO: