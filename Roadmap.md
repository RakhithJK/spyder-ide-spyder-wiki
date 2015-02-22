# Future

## Version 2.5 / December 2015
### Status: Planned

**New major features**:

* Debugger
    - Greatly improve debugging experience
* Object Inspector
    - Add class and constructor docstrings to the shown info (if available).
    - Add search facilities  


## Version 2.4 / February 2015
### Status: Early Stage of Development

**New major features**:

* IPython:
    - Notebook plugin to run notebooks natively inside Spyder (pull request #77)
    - Drop support for version 0.13
    - Pygments highlighting for the console
* Additional support for PyQt5 (along with our current PySide/PyQt4 support) (pull request #76)
* Conda Package Manager to install/uninstall packages included in Continuum repositories (pull request #61)
* Interactive tutorial (similar to the IPython notebook one) (pull request #70)
* Custom Layouts
    - pull request #65
    - Support for Matlab, RStudio and new defaults (horizontal/vertical layouts).
    - New shortcuts
    - Save as many named layouts as the user wants
* Editor Enhancements:
    - Code folding support (pull request #56)
    - Markdown and Restructured text support
* History Log:
    - Better support for IPython cells

----

# Present

## Version 2.3.3 / December 2014
### Status: Under Development

* Mainly about bug fixes

## Version 2.3.2 / November 2014
### Status: Under Development

**New major features**

* Editor
    - Improve cells visualization (pull request #51)
    - Add support for drag selection and improve look of line number area (pull request #51)
    - Open any text file present in the Variable Explorer (pull request #63)
    - View and edit IPython notebooks as Json files (pull request #32)
    - Syntax highlighting for Json files (pull request #32) 
* Variable Explorer:
    - Import csv files as DataFrames (if Pandas is present) (pull request #63)
* Debugging
    - Make it easier to set conditions on breakpoints (pull request #39)
* Python Console
    - Fixes various issues with unicode (pull request #83)

## Version 2.3.1 / September 2014
### Status: Maintenance

**New major features**:

* Variable Explorer
    - Support for Pandas DataFrame's and TimeSerie's types (pull request #31)
    - Support for Numpy 3D arrays (pull request #38)
    - Drag and drop works for all its supported file types (e.g. images, mat files, json files, etc) (pull request #4)
* Editor
    - F9 runs the current line under the cursor if nothing is selected
    - Focus remains on it after evaluating cells and selections (an option was added to return to the old behavior)
      (pull request #66)
* IPython console
    - Connect to external kernels through ssh (pull request #20)
* Object Inspector
    - Add a tutorial for beginners (pull request #11)
* Main Window
    - Improve style on Mac (pull request #64)

## Version 2.3 / July 2014
### Status: Maintenance

The main purpose of this release is to support officially Python 3 and improve our user interface (reorganize menu, improve startup time, etc)

**New major features**:

* Python 3 support
* Editor
    - Use the Tab key to do code completions
    - Highlight cells, i.e. portions of a file delimited by separators of the form `# %%`
    - First-class support for Enaml files
    - Syntax highlighting for Julia files
    - Use Shift+Tab to show the signature corresponding to a function/method while it's been called
    - Do code completions using the tokens (or words) found in a file
    - Token-based completions work for any file type supported by the Editor
    - Add a new tooltip widget (borrowed from the IPython project) to better handle how to show function signatures
* IPython console
    - Assign the keyboard shortcut Ctrl+Shift+I to move to it
    - Open a console by default at startup
    - Give visual feedback when opening a console
    - Show kernel error messages in the client tab
* Object Inspector
    - Add an intro message to explain how to use it
    - New style based on the Bootswatch Cerulean theme

-----------

# Past
## Version 2.2 / May 2013
### Status: Deprecated

**New major features**:

* IPython:
    - v0.13+ integration.
    - Add a Preferences entry and improve the new plugin named "IPython" which embeds the new Qt based IPython Qt frontend.
* Variable explorer:
    - Data Import Wizard: support more options inspired from (but less permissive than) numpy.loadtxt
* Debugging:
    - Add debug actions (toolbar with buttons) to go to next step, jump to next breakpoint, and so on
    - Add a new breakpoints plugin
    - Fix issues related to breakpoints being located in the wrong place.
* Editor:
    - Improve code completion

## Version 2.1 / Nov. 2011
### Status: Deprecated

Spyder v2.1 will be compatible with:

* PyQt's API #1 (i.e. compatible with PyQt 4.4 and 4.5)
* and PyQt's API #2
* and mostly with PySide.

**New major features**:

* New Profiler plugin
* Outline (function/class browser) is now a plugin in itself
* Editor:
    - Syntax highlighting: support for OpenCL, gettext files, CSS and HTML files
    - Support for "2 spaces" and "tabs" indentation characters
    - Find/replace: add options (multiline regexp find/replace support, highlight results...)

**Special versions**:

* v2.1.12: portable version of Spyder (i.e. a version handling settings in a Windows portable way), included in first release of WinPython 2.7, the portable Python distribution for Windows
* v2.1.13: last stable release of the v2.1 branch
* v2.1.14: experimental release providing Python 3 support, included in first release of WinPython 3.3

## Version 2.0 / Sept. 2010
### Status: Deprecated

**New major features**:

* The whole interface has been rewritten from scratch. Menus, options and plugins were also considerably simplified.
* User Module Deleter: deeply reload Python modules when necessary
* Preferences dialog box
* Customizable keyboard shortcuts
* Customizable syntax colors
* Consoles: white/black background
* IPython integration is no longer experimental
* Object Inpsector rich text mode (powered by Sphinx)

## Version 1.1 / June 2010
### Status: Deprecated

**New major features**:

* IPython integration
* New Online Help plugin (Doc viewer has been renamed to Object Inspector)

## Version 1.0 Final / Oct. 2009
### Status: Deprecated

** New major features**:

* Editor:
    - Vertical/horizontal splitting capabilities
    - Pylint integration
* History log:
    - 3 history logs instead of one (interactive console, external console/Python, external console/Terminal)
* Documentation
* External console:
    -  Real introspection capabilities (doc viewer, completion), globals browser (like interactive console's worskpace)

## Version 0.4 / May-Aug. 2009
### Status: deprecated

Spyder 0.4.x releases will be development snapshots, i.e. with new features and unfortunately new bugs for each new version. When all v1.0.0 features will be implemented (probably in June), v1.0.0 alpha, beta and release candidate versions will be released