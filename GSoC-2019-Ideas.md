# GSoC 2019 Project Ideas

## 1. Add Git/Gitub integration to Spyder

This purpose of this project is to create an external plugin that allows users to work comfortably with Git repositories in Spyder and also to submit their work to Github. In particular, this work should allow users to:

1. Review the status of repository (i.e. modified, added, deleted files).
2. View the diff of each file.
3. Commit work to the git repo, either in total or by hunks.
4. Browse git history.
5. View `git blame` and `git log` for each file.
6. Be able to easily define or create a remote on Github.
7. View current active branches and change between them.

### Motivation

This would allow scientists and engineers to easily keep track of their coding efforts through an easy to use graphical user interface.

### Expected Skills

Familiarity with Python, PyQt5, Git and Github.

### Available Mentors

* Carlos Cordoba (@ccordoba12)
* C.A.M. Gerlach (@CAM-Gerlach)

## 2. Update and improve *spyder-reports*

[`Spyder-reports`](https://github.com/spyder-ide/spyder-reports) is a third-party plugin developed when we were sponsored by Anaconda and whose aim is to create scientific reports from markdown files.

This project will update `spyder-reports` to work with the latest versions of Spyder and Pweave (our backend renderer). Besides, it'll add the ability to view reports in pdf format inside Spyder, improve markdown rendering in Spyder (e.g. code fences are not syntax highlighted right now) and extend markdown syntax in Pweave to add things like citations and cross-references.

### Motivation

Although Jupyter notebooks are a great reporting facility, they have a really critical problem that affects reproducibility: cells can be executed in any order, which can cause that the results present in a report depend on the current state of evaluation. That's why sometimes is preferable a tool that uses a linear and repeatable order of execution. 

### Expected Skills

Familiarity with Python, PyQt5 and Markdown.

### Available Mentors

* Carlos Cordoba (@ccordoba12)
* C.A.M. Gerlach (@CAM-Gerlach)