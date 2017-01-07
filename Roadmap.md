## Version 4.0 / December 2017

**New major features**:
* Global 
  - Provide a public API for third-party plugins to use it
  - Decouple widgets of its tight association with Python so they can be
    used by other languages (e.g. Julia and R).
* Editor
  - Bookmarks (See [Matlab Bookmarks](http://blogs.mathworks.com/community//2007/06/15/scroll-less-with-editor-bookmarks/))
  - Code folding support
  - Comment/Uncomment for all languages
  - Give warnings and error messages for other languages besides Python
* History Log:
    - Better support for IPython consoles

## Version 3.2 / June 2017

**New major features**:
* Editor
    - Make code completion to work on the fly
    - Markdown and Restructured text support
    - Improve Pygments integration
    - Tabs reordering
    - Make the File Switcher to open files of the current project
* Projects:
    - Add the ability to associate a virtual or conda environment with a project
    - Conda Package Manager to install/uninstall packages
* Settings
    - Emacs and RStudio keyboard shortcut sets
* IPython Console
    - Make it use the current Spyder color scheme theme