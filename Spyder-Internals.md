This section aims to give an introduction into Spyder internals.

**Note: This is a work in progress!**

# Directory Structure

The following tree represents the current structure of Spyder master repo. The branches here represent only folders, more specifics and explanations will be given below.


:open_file_folder: [spyder-ide/spyder.git](https://github.com/spyder-ide/spyder)       <br>
├── [app_example](#app_example)                                                        <br>
├── [doc](#doc)                                                                        <br>
├── [external-py2](#external-py2)                                                      <br>
├── [external-py3](external-py3)                                                       <br>
├── [img_src](#img_src)                                                                <br>
├── [rope_profiling](#rope_profiling)                                                  <br>
├── [scripts](#scripts)                                                                <br>
├── [spyderlib](#spyderlib) ··························· *Main library*                               <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [defaults](#defaults) ······················ *TODO:*                    <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [images](#images) ······················· *TODO:*                       <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [locale](#locale) ························· *Translations*              <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [plugins](#plugins) ······················· *TODO:*                     <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [qt](#qt) ······························· *PySide/PyQt wrapper*                       <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [utils](#utils) ···························· *TODO:*                    <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [widgets](#widgets) ······················ *TODO:*                      <br>
│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [externalshell](#externalshell) ······· *TODO:*<br>
│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;└── [sourcecode](#sourcecode) ········· *Code editor widget, Syntax highlighting*    <br>
│&nbsp;&nbsp;&nbsp;&nbsp;└── [windows](#windows) ···················· *TODO:*                        <br>
└── [spyderplugins](#spyderplugins) ·················· *TODO:*                                       <br>

## app_example
TODO:

## doc
As the name suggests this is the folder where the documentation of the project resides. 

The documentation is written in [reStructuredText](http://docutils.sourceforge.net/rst.html) (.rst) and is parsed using [Sphinx](http://sphinx-doc.org/).

The documentation is hosted in [Python Hosted](https://pythonhosted.org/spyder/).

## external-py2
Spyder makes use of external python libraries, such as [pyflakes](https://github.com/pyflakes/pyflakes/), [rope](http://rope.sourceforge.net/), [pep8](https://github.com/jcrocholl/pep8) and a modified version of the [conda_api](https://github.com/conda/conda-api). When Spyder runs from a Python 2 interpreter, the `external-py2` folder is added to the `PATH`. 

The modules saved here must be compatible with Python 2

## external-py3
Spyder makes use of external python libraries, such as [pyflakes](https://github.com/pyflakes/pyflakes/), [rope](http://rope.sourceforge.net/), [pep8](https://github.com/jcrocholl/pep8) and a modified version of the [conda_api](https://github.com/conda/conda-api). When Spyder runs from a Python 3 interpreter, the `external-py3` folder is added to the `PATH`. 

The modules saved here must be compatible with Python 3

**Note: Even if the same module works with both Python 2 and Python 3, it must be copied inside both `external-py2` and `external-py3` folders.**

## img_src
This folder holds the editable and rendered versions of images and art for the Spyder project.

Included files: Official icons, main logo, and some screenshots.

## rope_profiling
TODO:

## scripts
TODO:

## spyderlib
This is the actual main module of Spyder.

The name spyderlib is due to the existence of another project with the spyder 

### locale 
The translations of the interface for Spyder is stored in this folder. Currently Spyder has translations for Spanish (es) and French (fr). 

If you would like to have Spyder translated to a new language please drop us a line on the [public chat](https://gitter.im/spyder-ide/public).

### plugins
TODO:

### qt
Spyder is and will remain compatible with the available Qt bindings, [PyQt](http://www.riverbankcomputing.co.uk/software/pyqt/intro), and [PySide](http://qt-project.org/wiki/PySide).

This folder contains the modules that detect the available binding and wrap the necessary classes inside a single code base so that instead of using `import PySide.QtCore` or `import PyQt4.QtCore` we can use `import spyderlib.qt.QtCore`.
### widgets
TODO:

#### externalshell
TODO:

#### sourcecode
TODO:

### spyderplugins
TODO:
