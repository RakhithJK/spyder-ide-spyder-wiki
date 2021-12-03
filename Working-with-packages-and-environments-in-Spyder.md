While relatively straightforward once you're familiar with it, the interaction between Spyder and other packages and environments can sometimes be confusing for first-time users. Improvements to Spyder have made this process much easier (and there is more to come!), but we'd like to clarify how that relationship works.

We'll start by helping you to debug a common problem encountered in Python when dealing with packages and environments, i.e. when you can't import a module even if you're sure that you've installed it. Next, we'll guide you through setting up your Spyder environment(s) to improve your workflow. If you're looking for a way to use Spyder with different environments (e.g. one for simple data analysis, one for machine learning, one for developing an app, etc.) you can go directly to the [final section](#the-modular-approach).


- [The most common problem: Using newly-installed packages inside Spyder](#the-most-common-problem--using-newly-installed-packages-inside-spyder)
- [Installing packages into the same environment as Spyder](#installing-packages-into-the-same-environment-as-spyder)
- [Working with other environments and Python installations](#working-with-other-environments-and-python-installations)
  * [The naive approach](#the-naive-approach)
  * [The modular approach](#the-modular-approach)


### The most common problem: Using newly-installed packages inside Spyder

After installing a package (let's call it `foo`) outside Spyder, users may encounter an error trying to import it inside the IDE:

```python
In [1]: import foo
Traceback (most recent call last):

  File "<ipython-input-4-7f58dd7fb72e>", line 1, in <module>
    import foo

ModuleNotFoundError: No module named 'foo'
```

This happens because `foo` was installed (with either `conda` or `pip`) in a different conda or venv/virtualenv environment than the one in which Spyder is currently running.

To confirm this is the problem, you need to:

1. Activate the environment (*e.g.* `myenv`) in which you installed the package `foo` (*e.g.* with `conda activate myenv` for conda, `source myenv/bin/activate` or `workon myenv` for virtualenv/venv, *etc.*).

2. Start a Python interpreter there by running the command `python`.

3. Run the following command inside the Python interpreter:

   ```python
   import sys; sys.executable
   ```

4. Start Spyder and run the same command shown in Step 3 in a Console.

5. If the resulting paths are the same, then Spyder and the package are in the same environment, and `import foo` shouldn't produce an error (or else there is likely an unrelated issue with your installation).

6. If the resulting paths are different, then you have three choices:

   * Activate the environment in which Spyder is installed and install your package on it (see [next section](#installing-packages-into-the-same-environment-as-spyder)). If you try to install future packages in another environment (like `myenv`), you'll get the same `ModuleNotFoundError`.
   * Install Spyder into the existing `myenv` environment, or any other you'd like to work in, and run it from there (see [following section](#the-naive-approach)). This is a little simpler than the third option and has the same effect, but more overhead and is less flexible.
   * Install just the `spyder-kernels` package into the `myenv` environment, and set your Python interpreter path in Spyder's Preferences to point to `myenv`'s Python executable (see the [final section](#the-modular-approach). This requires one more initial step, but requires less maintenance in the long run and avoids duplicate Spyder installs.


### Installing packages into the same environment as Spyder

Spyder is a Python package just like any other you may be used to, and so you can `import` any package  within its *Console* or *Editor* as you could from a regular Python or IPython terminal launched in Spyder's environment:

* If Spyder is installed via our standalone installers (as we recommend on Windows and macOS), this will be Spyder's built-in environment, which contains many popular scientific package, but cannot be modified, to avoid breaking Spyder itself.
* If Spyder is installed with Anaconda (as we recommend on Linux) and launched via a shortcut, from Anaconda Navigator or from Anaconda Prompt without modifying anything, this will be the default `base` Anaconda environment.
* If Spyder is installed via `pip` (experts only) and not into a `virtualenv`/`venv`, this will usually be whatever Python installation `pip` itself belongs to.
* If you use a system package manager (`apt-get`, `dnf`, `emerge`, etc) to install Spyder, this will typically be your system Python and its library of packages.
* If you installed Spyder into a specific environment (`conda-env` or `venv`), or it came with a pre-configured one (like those for Keras or TensorFlow) and launched it from there, it will only have access to packages from that environment.

Therefore, if you'd like to use a package with your existing Spyder install (*e.g.* importing it into your scripts, packages or a Spyder IPython console), the simplest way to do so is to install the package into the same environment in which you installed Spyder, typically by the same means you installed Spyder (`conda`, `pip`, package manager, etc). However, this is not possible if you've used a standalone installer, and if you're installing packages with `pip`, `conda-forge`, Github, or custom channels, working on multiple major projects at once, using prebuilt environments, or otherwise have more sophisticated needs, you'll likely want to use one or more separate environments for your packages. If so, the next section explains how.


### Working with other environments and Python installations

If you have an existing, pre-configured environment (such as for Keras or TensorFlow), are managing multiple environments (such as for development or testing purposes), or even would like to work within a totally separate Python installation as that in which Spyder is installed (such as a standalone installer Spyder with a separate Anaconda installation, or vice-versa), you can install the modular `spyder-kernels` package into any Python environment (`conda` environment, `virtualenv/venv`, system Python, WinPython, *etc*) in which you wish to work, and then change the Python interpreter used by Spyder on its IPython consoles to point to the Python executable of that environment.

This takes a small amount of preparation and configuration, but is much "lighter" and quicker than a full Spyder installation into that environment, avoids dependency conflicts, and opens up new workflow possibilities.

To achieve this, follow these steps:

1. Activate the environment (*e.g.* `myenv`) in which you'd like to work (*e.g.* with `conda activate myenv` for conda, `source myenv/bin/activate` or `workon myenv` for virtualenv/venv, *etc*)

2. Install the `spyder-kernels` package there, with the command:

   * `conda install spyder-kernels` if using conda/Anaconda,

   * `pip install spyder-kernels` if using pip/virtualenv.

3. After installing via either method, run the following command inside the same environment:

   ```python
   python -c "import sys; print(sys.executable)"
   ```

   and copy the path returned by that command (it should end in `python`, `pythonw`, `python.exe` or `pythonw.exe`, depending on your operating system).

4. Deactivate that environment, activate the one in which Spyder is installed (if you've installed it in its own environment) and start Spyder as you normally would.

5. After Spyder has started, navigate to `Preferences > Python Interpreter > Use the following interpreter` and paste the path from Step 3 into the text box.

6. Start a new IPython console. All packages installed in your `myenv` environment should be available there. If conda is used, the name of the current environment and its Python version should be displayed in Spyder's status bar, and hovering over it should display the path of the selected interpreter.

**Notes:** 
* In order for the Variable Explorer to be able display the built-in editors for specific data types (Numpy array, Pandas Series/DataFrame, etc) the corresponding optional Spyder dependencies (Numpy, Pandas, etc) need to be installed in Spyder's environment, not just the IPython console working env. Furthermore, this is currently also required for custom classes provided by third-party packages displayed in the Object Explorer, though future Spyder versions may remove this latter limitation.  
* While Spyder should work fine without it, ensuring the Python minor version (`3.6`, `3.7`, `3.8`, etc) in Spyder's environment matches that in your working environment, if practicable, will minimize the chance of any issues.