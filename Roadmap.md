## Version 4.0 / June 2018

**New major features**:
* Global 
  - Provide a public API for third-party plugins to use it
  - Decouple widgets of its tight association with Python so they can be
    used by other languages (e.g. Julia and R).
  - Make the File Switcher to open files of the current project
* Editor
  - Bookmarks (See [Matlab Bookmarks](http://blogs.mathworks.com/community//2007/06/15/scroll-less-with-editor-bookmarks/))
  - Code folding support
  - Comment/Uncomment for all languages
  - Give warnings and error messages for other languages besides Python
  - Make code completion to work on the fly
  - Restructured text support
* History Log:
    - Better support for IPython consoles
* Projects:
    - Add the ability to associate a virtual or conda environment with a project
* Settings
    - Emacs and RStudio keyboard shortcut sets