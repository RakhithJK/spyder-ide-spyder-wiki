## Roadmap for 2018

* **June 1**: *Spyder 4 beta 1* released, with all improvements developed while we were part of Anaconda, Inc.
    
  Also, *Spyder 3.3* released, with important bugfixes and enhancements to our stable branch including: 

  - Dropping support for Python 3.3 and PyQt 4
  - Fixes for several nasty memory leaks
  - Usability improvements

* **July 15th**: *Spyder 4 beta 2* released, with:
    - Language server protocol integration, to make our Editor use the best code completion architecture available.
    - A new ``ipdb`` kernel package to significantly improve debugging in Spyder. This package will also modualize the code used to create kernels that currently lives in Spyder itself.

* **September 1st**: *Spyder 4 beta 3* released, with:
    - Major enhancements to projects, including the ability to define a ``conda``/``pip`` environment per project, graphical installation of packages in that environment and the use of ``cookiecutter`` templates to create projects.
    - Integrating the new ``ipdb`` kernel with Spyder, to enable syntax highlighting, code completion, history browsing and plotting while debugging (our most-requested new feature).

* **November 1st**: *Spyder 4 beta 4* released, with:
    - A new icon theme, based on the Breeze theme used in KDE.
    - A new dark theme for the entire application.
    - Keyboard shortcut presets, to allow users to easily set up their hotkeys to emulate RStudio, Emacs or Sublime Text.
    - Full support for viewing any object in the Variable Explorer (Currently, only Dataframes, NumPy arrays and builtin iterables are properly supported).

* **December 15th**: *Spyder 4 release candidate 1*, with bugfixes and polish on the newly added features above