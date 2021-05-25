# Build Spyder on macOS

To build Spyder's standalone application for macOS you need:

* Python 3.x installed, not from Anaconda and not your native Python installation (2.7).
* A local clone of the [Spyder Project](https://github.com/spyder-ide/spyder) repository.
* A virtual environment in which to install the necessary packages

Once you have the above requirements, you will build the application from within your virtual environment.
The following sections will take you through the entire process.

## Install Python 3.x

In principle, it doesn't which Python installation you use except it cannot be your native system Python (because it is 2.7) or Anaconda.
The Anaconda installation does not work because its Python libraries are not structured in a way that allows them to be packaged in a macOS application.

We recommend using [Homebrew](http://brew.sh/) to install `pyenv` and `pyenv-virtualenv`, which will allow you to install whichever Python version you wish.

Install Homebrew with the following in a Terminal.
```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
After installing Homebrew, run
```bash
$ brew install tcl-tk, pyenv, pyenv-virtualenv, xz
```
`tcl-tk` is a package of Tcl/Tk libraries required when using Tkinter with Python.
`pyenv` and `pyenv-virtualenv` are command line applications for installing and managing Python environments.
`xz` is a package that provides compression algorithms that Python should be built with to satisfy some packages, namely `pandas`.

## Clone the Spyder Repository

Clone Spyder's repository to a local directory of your choice.
```bash
$ git clone https://github.com/spyder-ide/spyder.git <directory>
```
Having a git repository is useful in that it will allow you to pull updates to the code easily, or allow you to checkout certain versions.

## Create the Virtual Environment

The Python frameworks must be copied to the stand-alone application, so when setting up a virtual environment you must set certain flags.
```bash
$ export TKPREFIX=$(brew --prefix tcl-tk)
$ export PYTHON_CONFIGURE_OPTS="--enable-framework --with-tcltk-includes=-I${TKPREFIX}/include --with-tcltk-libs='-L${TKPREFIX}/lib -ltcl8.6 -ltk8.6'"
```
Now you can install Python. The following installs Python 3.9.4, but you may use whichever version you like (>=3.7).
```bash
$ pyenv install 3.9.4
```
Next you will create and activate the virtual environment.
You may name it whatever you like, but for this example we will name it `spy-build`.
```bash
$ pyenv virtualenv 3.9.4 spy-build
$ pyenv activate spy-build
```

## Build Spyder

First you must checkout the commit in the Spyder repository that you wish to build.
This can be any commit, but for this example we will build Spyder version 5.0.3.
Change your working directory to the Spyder repository and checkout the appropriate commit.
```bash
$ cd <directory>/spyder
$ git checkout v5.0.3
```

Now you will install the build, extras, and scientific packages from requirements files located in the repository.
Spyder's dependencies will be installed by installing Spyder from the source code.
However, Spyder itself will be uninstalled so as not to interfere with the build process.
You should still be in your `spy-build` environment.
```bash
$ pip install -U pip setuptools
$ pip install -r installers/macOS/req-build.txt -r installers/macOS/req-extras.txt -r installers/macOS/req-scientific.txt -e .
$ pip uninstall -q -y spyder
```

If you build Spyder from non-release commit, you will need to install the developer versions of `spyder-kernels`, `python-language-server`, and `qdarkstyle` provided in subrepos to Spyder's repository.
```bash
$ pip install -e external-deps/spyder-kernels -e external-deps/python-language-server -e external-deps/qdarkstyle
```

You are now ready to build the standalone application.
```bash
$ cd installers/macOS
$ python setup.py
```
After a whole lot of screen dump, and if everything went well, you should now find the application bundle at `<directory>/spyder/installers/macOS/dist/Spyder.app`.

You can get a list of options for `setup.py` as follows.
```bash
$ python setup.py -h
```

# Building Spyder on Windows

