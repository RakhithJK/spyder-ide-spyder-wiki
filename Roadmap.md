## Version 4.0 / September 2017

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
  - Make code completion to work on the fly
  - Make the File Switcher to open files of the current project
* History Log:
    - Better support for IPython consoles
* Projects:
    - Add the ability to associate a virtual or conda environment with a project
* Settings
    - Emacs and RStudio keyboard shortcut sets

## Version 3.2 / June 2017

**New major features**:
* Editor
    - Improve Pygments integration
    - Tabs reordering
    - Restructured text support
* Python Console:
    - Remove it for all operating systems
* Find in files
    - Several improvements to make it more usable
* IPython Console
    - Make it use the current Spyder color scheme theme