# GSoC 2019 Project Ideas

## Add Git/Gitub integration to Spyder

This purpose of this project is to create a Spyder plugin that allows users to work comfortably with Git repositories in Spyder and submit their work to Github. In particular, this plugin should allow users to:

* Browse current active branches and change between them (from `git-cola`).
* View `git diff`, `git log` and `git blame` for each file, and launch the `git mergetool` if a merge conflict is detected (from `git-cola`).
* See an indicator of lines changed, added and removed in an Editor gutter panel (like [VSCode offers](https://code.visualstudio.com/docs/editor/versioncontrol#_gutter-indicators))
* Commit work to the git repo with a commit message, either in total or by hunks (from `git-cola`).
* Explore git history (with `qgit`).
* Be able to easily define or create a remote on Github.


### Motivation

Better Git/Github integration is perhaps the most-requested Spyder feature by our users that has not yet been implmeneted or scheduled for implementation. This would allow scientists, engineers and data analysts to much more easily employ powerful VCS tools to greatly aid reproducibility and reusability of their code and share them with the world, all within a familiar graphical user interface.

### Expected Skills

Familiarity with Python, PyQt/PySide, Git and Github.

### Available Mentors

* Carlos Cordoba (@ccordoba12)
* C.A.M. Gerlach (@CAM-Gerlach)


## 2. Update and improve *Spyder-Reports*

[Spyder-Reports](https://github.com/spyder-ide/spyder-reports) is a Spyder plugin developed to allow users to create dynamic, rich text documents incorporating code blocks, Markdown prose, and dynamically updated output and figures/visualizations, all within Spyder. The goal is to bring the power and functionality of a tool equivalent to Sweave/Knitr and R Markdown to a Python IDE.

This project will update `spyder-reports` to work with the latest versions of Spyder and ``pweave`` (our backend renderer). In additional, it'll add the ability to view reports in PDF format inside Spyder, improve markdown rendering in Spyder (e.g. code fences are not syntax highlighted right now), extend the syntax in Pweave to add features like citations and cross-references, and add support for LaTeX as well as Markdown for scientific output, as this is already fully implemented in ``pweave``.

### Motivation

Although Jupyter notebooks can be a good reporting facility for some applications, they offer critical shortcomings for many others: they require Jupyter Notebook to view them, along with all the dependencies of the original work; they are often unworkable for projects with large datasets or long compute times as they most be executed dynamically, they are not self-contained, cells can be executed in any order and have other unexpected quirks harming reproducibility. Meanwhile, presenting raw Python code requires either sharing the source files with all their extra cruft and inaccessibility to non-experts, and without contextual prose, output or plots; or manually copying and pasting code, output and figures into a separate document, and having to update everything by hand when anything changes.

Therefore, integrating the capabilities of ``pweave`` with Spyder allows researchers and professionals to easily write up and share their work and results with colleagues, managers and the public at large, and also enables the creation of informative guides, tutorials and even whole textbooks, all within Spyder.

### Expected Skills

Familiarity with Python, PyQt/PySide and Markdown or LaTeX. Experience using ``pweave``, Sweave, or R Markdown a plus.

### Available Mentors

* Carlos Cordoba (@ccordoba12)
* C.A.M. Gerlach (@CAM-Gerlach)