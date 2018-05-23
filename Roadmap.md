## Roadmap for 2018

* **June 1**: Release of Spyder 4 beta 1, with:
    - All improvements developed while we were part of Anaconda, Inc.
    - Also release of Spyder 3.3, with important bugfixes to our stable branch (e.g. drop support for Python 3.3 and PyQt 4 and fix some nasty memory leaks).

* **July 15th**: Release of Spyder 4 beta 2, with:
    - Language server protocol integration, to make our Editor use the best code completion architecture available.
    - Creation of an ipdb kernel package to significantly improve debugging in Spyder. This package will also contain the code used to create kernels that currently lives in Spyder.

* **September 1st**: Release of Spyder 4 beta 3, with:
    - A much improved projects support, which includes the ability to define a conda/pip environment per project, graphical installation of packages in that env and the use of cookiecutter templates to create projects.
    - Integration of the ipdb kernel within Spyder, to have syntax highlighting, code completion, history browsing and plotting while debugging (this is the most asked feature by our users, by the way).

* **November 1st**: Release of Spyder 4 beta 4, with:
    - A new icon theme, based on the Breeze theme used in KDE.
    - A new dark theme for the entire application.
    - Shortcut sets, to allow people set in one action the default set of shortcuts used in RStudio, Emacs or Sublime Text.
    - Support to view any object in our Variable Explorer. Right now we only support Dataframes, NumPy arrays and builtin iterables (lists, dicts, tuples and sets).

* **December 15th**: Release of Spyder 4 rc1, with bugfixes only on the new features added so far.