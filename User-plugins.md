# User Plugins

**NOTE: These informations apply to Spyder V3.0 onwards (starting from 3.0.0b3 exactly) !**

Spyder capabilities can be enhanced by installing plugins. There are currently two plugin types:

* **UI plugins**: These plugins add a new pane or a new menu action. Examples are Pylint, Profiler and Breakpoint plugins, which are shippêd with spyder by default.
* **IO plugins**: With these plugins Spyder can learn to load and save different file formats from the variable explorer

Some plugins are developed by core developers and can be found on github:
* [spyder.line_profiler](https://github.com/spyder-ide/spyder.line_profiler)
* [spyder.memory_profiler](https://github.com/spyder-ide/spyder.memory_profiler)
* [spyder.autopep8](https://github.com/spyder-ide/spyder.autopep8)
* [spyder.vim](https://github.com/spyder-ide/spyder.vim) (_in development_)
* [spyder.unittest](https://github.com/spyder-ide/spyder.unittest) (_in development_)
* [spyder.terminado](https://github.com/spyder-ide/spyder.terminado) (_in development_)

We hope to see more plugins written by users in the future !

## Install
Plugins are python packages with a name starting with `spyder_`. They are loaded from anywhere in `sys.path` or in `${HOME}/.spyder/plugins/`. There are multiple ways to install a plugin:
* with `pip` and PyPi: `pip install <PLUGIN.NAME>` (note that pypi versions of core plugins are not up-to-date as of today)
* with `pip` without PyPi: Download and unzip (or clone) a plugin and run `pip install .` or `python setup.py install` from inside the plugin  directory
* copy-paste: Download and unzip (or clone) a plugin and copy the directory starting with `spyder_` in `${HOME}/.spyder/plugins/`
* install last development version: `pip install git+git://github.com/spyder-ide/<PLUGIN.NAME>.git`

You have to restart spyder for the modifications to be taken into account (Menu _File_ > _Restart_).

## Uninstall
If the plugin was installed with `pip`, run `pip uninstall <PLUGIN.NAME>`.
If the plugin was copy-pasted in `${HOME}/.spyder/plugins/`, just remove its directory.