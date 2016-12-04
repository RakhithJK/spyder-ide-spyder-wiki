## Version 3.1dev

### New features

#### Editor
* Add the Solarized Light and Dark color schemes.
* Add support for greedy regular expressions in the find/replace widget
  (only available under PyQt5).
* Improve the use of tabs instead of spaces for indentation.

#### Variable Explorer
* Add support for the most important numeric types of Numpy (int, float
  complex numbers of 32 and 64 bits).
* Save format for floats in DataFrame editor.

#### IPython Console
* Be able to load kernel json files anywhere in the file system when
  connecting to external kernels.

#### Settings
* Make all keyboard shortcuts configurable

#### Under the hood
* Add the chardet library as a new dependency.


----


## Version 4.0dev

### New features

#### Python Console
* Disconnect it from the Variable Explorer

#### API Changes
* Create the module `spyder.api` to expose a public API

##### Major changes

##### Minor changes
