| key            | value                                                 |
|----------------|-------------------------------------------------------|
| Status         | Active                                                |
| Author         | Full Name &lt;full.name@gmail.com&gt;                 |
| Created        | February, 2015                                        |
| Updated        | February, 2015                                        |
| Discussion     | link to the issue where the SEP is being discussed    |
| Implementation | link to the PR                                        |

# Conversation and comments
I recently discovered [Gitter](Gitter.im) and seems like a nice place to have some discussions, includes markdown support and could be used to have specific discussions on this feature.

# Current status
There is a basic project management in Spyder that works using a main **workspace** where all the project folder are stored. For project management there is currently a `Project Explorer` panel that is basically the `File explorer` panel plus some options.

When creating a workspace a binary file `.spyderworkspace` is created. Projects stored in this folder (as subfolders) will create a binary file `spyderproject`.

Projects are created via the `New project..` option in the `File` menu, or directly in the `Project Explorer` widget.

Version control right now just tries to open any existing program on the OS to run commits (e.g. tortoise hg). 

# Proposal
The idea is to bring the project support up to date, to clean up the existing code, and merge the outline explorer widget with the project explorer widget.

The project explorer panel as it is nowadays seems to be redundant (several users have expressed this) and seems to bring more confusion than clarity to the Spyder interface. The `File explorer` should be able to handle exploring files and the outline explorer should be extended to display the files and folder belonging to a specific project.

**Modifications suggested**
* The actual created binary files should be changed to a readable format and store the basic information of a project.

* There should be built-in support for version control. This is work for another proposal, but the machinery for this can be left in place.
* There should be no need for a workspace directory. Projects should be created in any folder where needed.
* A project should link a series of things together, including:
    * A set of last used files could be opened in the editor
    * An Ipython session
    * Command history specific to the project?
    * Workspace (All variables in the object inspector upon exit)
    * The complete state of the consoles (implementing with [dill](https://github.com/uqfoundation/dill))

* When opening or creating a new project, all the files in the editor should be closed and replaced with 
the ones pertaining  to the project (an empty file if a new project). The last Ipython session could be restored as well?

Some of these options could be stored in the .spyderproject file, but other might need a folder (.spyderprojectdir?). For instance we could use this directory to store the environments (either conda or virtual env) as to not pollute the project directory with many folders.

## Projects files
A .spyderproject file could be created, but this file should be in a human readable format, and contain information relating to description of the project etc...

The proposed format is JSON

## Environments
Reproducible science is a key component in Scientific Research and one way to replicates someone else work when working with code is through the use of environment. The use of environments should be optional, but should also be encouraged when aimed at sharing work/results etc...

There are two options to work here:
* Use [conda](https://github.com/conda/conda) to create environments. This would only work when using the anaconda distribution, and would leverage from the work done in the **Conda Package Manager Plugin**. This works in a cross platform way, but would force users to use this distribution. If this option is used the `Conda Package Manager Plugin` would handle the installation of packages inside the project.
* Use [virtualenv](https://github.com/pypa/virtualenv). This would work for users not using anaconda, but would have some limitations for nonpython libraries and dependencies not handled by **pip** or the like. there could be something like a `Pip Package Manager?` to be used in this cases?

## Version Control
This will be developed in a separate [proposal](https://github.com/spyder-ide/spyder/wiki/SEP-1:-Version-Control). The idea is to have a basic abstraction layer and support for different version control systems, namely Git and Mercurial. [Issue 816](https://github.com/spyder-ide/spyder/issues/816) started the discussion and will serve as basis for this PR.

The plan is to have a minimal set of features that would allow common vc commands to be used inside spyder by calling the external programs (using a QProcess) or by using an already established external module.

## Interface

### Menu
The entry point from the file menu would remain the same, but it would call a more elaborate dialog 

### Main projects dialog

The basic proposed layout is something like:



The main dialog would include (subdialogs as subbullets):
* Create New Project
    * Create empty project
    * Create Python Package
    * Create ...
    * Create Django Project?  (available if django is detected and could be a plugin?) 
    * Create Pelican Project?  (available if pelican is detected and could be a plugin?) 
* Import From Existing Directory
* Import from version control (if git or mercurial detected, otherwise grey out?)
    * Git (if detected)
    * Hg  (if detected)

Depending on the option selected and the available programs, the user could select to include version control in a project, and to create new environment selecting the python version to use in the project. The options would adjust or grey out depending on availability or distribution used.

### Projects toolbar
A new toolbar could be created consisting of a dropdown combobox with the listing of recently created projects (this would be stored in the spyder.ini file and if not found on startup, would not displayed) , and a setup button with some options (including creating a new project or opening a new project).

A project could also be opened through the file explorer, if a folder contains a .spyderproject, the icon could change and when double clicked a pop dialog could ask if you want to open the project. If the user accepts opening this would add this to the combobox as recently used project

## Projects to support
Initially there should be support for basic projects such as simple container for a bunch of scripts in version control and a specific environment, and a Python package. The plugin could be thought from the start to be extendable with plugins?, to offer support for other projects

### Python packages
This projects could include a basic setup for including a `readme.md` file, a .**ignore file and the basic structure including a `setup.py` etc..
 
## Future Projects to support?
Support for more project types could grow gradually in the form of plugins

### Django?


### Pelican?


### Others?
