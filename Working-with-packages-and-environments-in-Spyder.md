While relatively straightforward once you're familiar with it, the interaction between Spyder and other packages and environments can sometimes be confusing for first-time users.
Spyder 4 will make this process much easier with integrated, interactive GUI package and environment management, but in the meantime —particularly with the changes in the released Spyder 3.3.0— we'd like to clarify how that relationship works.


### The most common problem

The most common problem people find when installing a package (e.g. called `foo`) outside Spyder and then trying to use it inside it is that they get the following error

```python
In [1]: import foo
Traceback (most recent call last):

  File "<ipython-input-4-7f58dd7fb72e>", line 1, in <module>
    import foo

ModuleNotFoundError: No module named 'foo'
```

This happens because you installed `foo` (either with conda or pip) in a different conda or venv/virtualenv environment than the one Spyder is running.

To avoid this problem, you need to

1. Activate your environment with `source activate myenv`, `workon myenv`, etc

2. Start a Python interpreter there by simply running `python`.

3. Run the following command on it

    ```python
    import sys; sys.executable
    ```

4. Start Spyder and run the same command shown in step 3. in one of its consoles.

5. If the results are the same, then things are fine and `import foo` shouldn't give you any error.

6. If the results are different, then you have two choices:

    1. Be sure to select the environment in which Spyder is installed (the one associated to the result you got in step 4.) and install your package on it. Installation on any other environment will always give `ModuleNotFoundError`.
    2. Follow one of the methods mentioned in the next section (you only need to use one of them, not both).


### Working with other environments and Python installations

If you have an existing, preconfigured environment (such as for Keras or TensorFlow), are managing multiple environments (such as for development or testing purposes), or even would like to work within a totally separate Python installation as that in which Spyder is installed (such as a system-installed Spyder with a separate Anaconda installation, or vice-versa), you have two main options:

#### 1. The easy approach

You can simply install `spyder` into the environment from which you'd like to use the packages in, and run it from there.

This works with all Spyder versions and it should require no extra configuration once Spyder is installed; however, it results in multiple Spyder installations to manage and isn't as flexible or configurable as the alternative.

#### 2. The modular approach

Starting with Spyder **3.3.1**, you can install the modular `spyder-kernels` package into any Python environment (`conda` environment, `virtualenv/venv`, system Python, WinPython, etc) in which you wish to work, and then simply change the Python interpreter used by Spyder on its IPython console to point to the Python executable of that environment.

This takes a small amount of preparation and configuration, but is much "lighter" and quicker than a full Spyder installation into that environment, avoids dependency conflicts, and opens up new workflow possibilities.

To achieve this, you need to follow these steps:

1. Activate your environment with `source activate myenv`, `workon myenv`, etc

2. Install the `spyder-kernels` package there, with the following commands:

       conda install spyder-kernels=0.*

   or

       pip install spyder-kernels==0.*

3. Also run there

       python -c "import sys; print(sys.executable)"

   and copy the path returned by that command (it should end in `python`, `pythonw`, `python.exe` or `pythonw.exe`, depending on your operating system).

4. Deactivate your environment and start Spyder from your root or base conda environment or the Python installation where you have Spyder installed.

5. After Spyder has started, please go to

    `Tools > Preferences > Python Interpreter > Use the following interpreter`

    and paste there the path you got in step 3.

6. Start a new IPython console. All packages installed in your `myenv` environment should be available there.


### Installing packages into the same environment as Spyder

Spyder is a Python package just like any other you may be used to, and so *by default* you can `import` within the Spyder console or editor any package you could from a regular Python or IPython terminal launched in the same environment as Spyder itself is installed and launched in:

* If Spyder is installed with Anaconda (as we recommend) and launched via a shortcut, from Anaconda Navigator or Anaconda Prompt without modifying anything, this will be the default `base` Anaconda environment.
* If Spyder is installed via `pip` (experts only) and not into a `virtualenv`/`venv`, this will usually be whatever Python installation `pip` itself belongs to.
* If you use a system package manager (`apt-get`, `dnf`, `emerge`, etc) to install Spyder, this will typically be your system Python and its library of packages.
* If you installed Spyder into a specific environment (`conda-env` or `venv`), or it came with a pre-configured one (like those for Keras or TensorFlow) and launched it from there, it will only have access to packages from that environment.

Therefore, if you'd like to use a package with an existing Spyder install (*e.g.* `import`'ing it into your scripts, packages or a Spyder IPython console), the simplest way to do so is to simply install the package into the same environment in which you installed Spyder, typically by the same means you installed Spyder (`conda`, `pip`, package manager, etc).