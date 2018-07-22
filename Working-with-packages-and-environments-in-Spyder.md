While relatively straightforward once you're familiar with it, the interaction between Spyder and other packages and environments can sometimes be confusing for first-time users.
Spyder 4 will make this process much easier with integrated, interactive GUI package and environment management, but in the meantime —particularly with the changes in the released Spyder 3.3.0— we'd like to clarify how that relationship works.


### Installing packages into the same environment as Spyder

Spyder is a Python package just like any other you may be used to, and so *by default* you can `import` within the Spyder console or editor any package you could from a regular Python or IPython terminal launched in the same environment as Spyder itself is installed and launched in:

* If Spyder is installed with Anaconda (as we recommend) and launched via a shortcut, from Anaconda Navigator or Anaconda Prompt without modifying anything, this will be the default `base` Anaconda environment.
* If Spyder is installed via `pip` (experts only) and not into a `virtualenv`/`venv`, this will usually be whatever Python installation `pip` itself belongs to.
* If you use a system package manager (`apt-get`, `dnf`, `emerge`, etc) to install Spyder, this will typically be your system Python and its library of packages.
* If you installed Spyder into a specific environment (`conda-env` or `venv`), or it came with a pre-configured one (like those for Keras or TensorFlow) and launched it from there, it will only have access to packages from that environment.

Therefore, if you'd like to use a package with an existing Spyder install (*e.g.* `import`'ing it into your scripts, packages or a Spyder IPython console), the simplest way to do so is to simply install the package into the same environment in which you installed Spyder, typically by the same means you installed Spyder (`conda`, `pip`, package manager, etc).

However, for more complex workflows involving environments or even totally separate Python installs, you have several other options.


### Working with other environments and Python installations

If you have an existing preconfigured setup (such as for Keras or TensorFlow), are managing multiple environments (such as for development or testing packages), or even would like to work within a totally separate Python installation as that in which Spyder is installed (such as a system-installed Spyder with a separate Anaconda install, or vice-versa), you have two main options:

* First, you can simply install `spyder` into the environment from which you'd like to use the packages in, and run it from there.
  This works with all Spyder versions and it should require no extra configuration once Spyder is installed; however, it can result in multiple Spyder installations to manage and isn't as flexible or configurable as the alternative.
* Starting with Spyder 3.3.0, you can now just install the modular `spyder-kernels` package into a Python environment (`conda-env`, `venv`, system Python, or even an independent installation) in which you wish to work, and then simply go to `Tools > Preferences > Python interpreter` in any running Spyder instance and change the path of the selected interpreter to point to the Python executable of that environment.
  This takes a small amount of preparation and configuration, but is much "lighter" and quicker than a full Spyder installation into that environment, avoids dependency conflicts, and opens up new workflow possibilities.

*Note:* If you go with the second option, make sure you install the correct version of `spyder-kernels` for the version of Spyder you are using: `0.x` for Spyder 3, and `1.x` for Spyder master branch. You can do this in `pip` or `conda` by specifying the version in the install command, e.g.

```bash
conda install spyder-kernels=0.*
```

or

```bash
pip install spyder-kernels==0.*
```

to get the Spyder 3 version (or replace the `0` with `1` for Spyder master).