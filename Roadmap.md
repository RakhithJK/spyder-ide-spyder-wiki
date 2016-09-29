# Future

## Version 4.0 / August 2017

**New major features**:

* All widgets 
  - Widget API improvement
  - Language agnostic widget decoupling

* Code Editor
  - Bookmarks (See [Matlab Bookmarks](http://blogs.mathworks.com/community//2007/06/15/scroll-less-with-editor-bookmarks/))


## Version 3.1 / December 2016
### Status: Planned

**New major features**:

* Global
    - Floating panes now behave as independent windows 
    - Emacs keybindings
    - VIM Keybindings
    - Editor Tab reordering

* Object Inspector
    - Add class and constructor docstrings to the shown info (if available).
    - Add search facilities
    - Live render support for Markdown and ReStructuredText files
* Source Code editor reorganization and language support (Cython, C, HTML, CSS)
    - Support for autoindentation
    - Support for completion
* Outline explorer
    - Display Markdown and ReStructuredText headers
* IPython Console
    - Drop support for IPython 3.0
    - Pygments highlighting for the console
* Editor
    - Code folding support
    - Markdown and Restructured text support
* Plugins:
    - Plugin manager 
    - Custom Plugins for spyder are now be pip installable
* New plugins:
    - Autopep8 plugin
    - Conda Package Manager to install/uninstall packages included in Continuum repositories
* History Log:
    - Better support for IPython cells

## Version 3.0 / September 2016
### Status: Maintenance

**New major features**:

* Global:
    - **DONE** New restart option from within Spyder
    - **DONE** Tab reordering for panes
    - **DONE** New default icon set (Spyder 3) based on QtAwesome
    - **DONE** Additional support for PyQt5 (along with our current PySide/PyQt4 support)
* Editor:
    - **DONE** Array builder
    - **DONE** Improved auto-completion widget
    - **DONE** File switcher (ala sublime)
* Projects:
    - **DONE** New project model
    - **DONE** Project preferences
* Interactive tutorial (similar to the IPython notebook one):
    - **DONE** Spyder exploration
* Custom Layouts
    - **DONE** Support for Matlab, RStudio and new defaults (horizontal/vertical layouts).
    - **DONE** Save as many named layouts as the user wants
* Preferences:
    - **DONE** New shortcut entry model, plus shortcut finder
    - **DONE** Select the language for the interface (English, Spanish, French or Portuguses)
    - **DONE** Reset to factory defaults from within Spyder
* Consoles:
    - **DONE** Array builder
* IPython:
    - **DONE** Drop support for versions 1.0 and 2.0
    - **DONE** Array builder