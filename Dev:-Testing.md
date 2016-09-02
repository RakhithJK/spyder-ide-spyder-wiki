We use testing to ensure that Spyder runs correctly in different environments. These tests are run automatically for every pull request. At the moment, the number of tests is not very large, but we hope that the coverage gradually increases over time by including tests in every change.

Most tests use the pytest framework, and this is what is described here. However, sometimes the tests are in the `if __name__ == '__main__'` block, so you have to run the .py file to run the tests. This is especially prevalent for widgets.


## Dependencies

The following components are needed in order to run the tests, in addition to the usual dependencies of Spyder:
* [pytest](http://pytest.org/latest/) is the framework that we use for testing.
* [pytest-qt](http://pytest-qt.readthedocs.io/en/latest/) is a plugin for pytest which we use for tests specific to Qt.
* [pytest-cov](http://pytest-cov.readthedocs.io/en/latest/) is a pytest plugin which produces coverage reports. You only need it if you plan to run the tests using `runtests.py` or if you want to generate coverage reports yourself.
* _mock_ is a library used to generate mock objects, which replace normal Spyder objects when testing. In Python 3, this is included as [unittest.mock](http://docs.python.org/3/library/unittest.mock.html) in the standard library, so you do not need to install anything. In Python 2, you need to install the back-ported [mock](https://pypi.python.org/pypi/mock) library separately.

These can be installed using conda or pip. When using conda, you need to bear in mind that pytest-qt is not distributed in the standard channel but in our own `spyder-ide` channel. Thus, you need the following commands (delete pytest-cov and mock if you don't need them):

```
conda install pytest pytest-cov mock
conda install -c spyder-ide pytest-qt
```

When using pip, the command is (again, delete pytest-cov and mock if you don't need them):

```
pip install pytest pytest-qt pytest-cov mock
```


## Running tests

There are basically two ways in which you can run the tests: using the `runtests.py` script provided by us, or directly using pytest.

When **using the runtests.py script** (which is in the root of the Spyder source tree), the command is simply `python runtests.py`. This is the easiest if you just want to see whether the tests pass or not. We use the `runtests.py` script to run the tests automatically on the Continous Integration servers and it sets up correctly. The disadvantage is a lack of flexibility: you cannot change any options, and it gives a lot of output that you may not need. Using the `runtests.py` script requires that `pytest-cov` is installed, otherwise you get the error message: `unrecognized arguments: --cov=spyder`.

When **using pytest directly**, the command is basically `py.test` (there are some gotchas, explained below). This runs all tests in the current directory and the subdirectories below it. See the [pytest docs](http://pytest.org/latest/) for further information, including the many options that can be used to control which tests are run.

If you use pytest directly, you need to make sure that the root of the Spyder source tree is included in the Python path, because the test files import `spyder` and its modules. You can use the `PYTHONPATH` environment variable for this. If you don't do this, then the tests will fail, or (if you have Spyder installed) they will test the installed version of Spyder.

If you want to specify the Python executable (for instance because you have multiple versions of Python installed), then you can use the command `python -m pytest` instead of `py-test`.

When using Python 2 and Qt 4, you may get the error message `API 'QString' has already been set to version 1`. The solution to this is to set the environment variable `PYTEST_QT_API` to `pyqt4v2`.


## Writing tests

Test coverage is rather sparse at the moment, but we want to expand this, so do not take the current lack of tests as a reason not to write any tests yourself. Ideally, every bug fix should come with a regression test (a test which checks that the bug is indeed fixed). Every pull request for a new feature should include tests for that feature.

The convention we use is that the test files for a certain Python file should be in a subdirectory called `tests`, located in the same directory as the file being tested. So tests for `spyder/plugins/editor.py` go in the `spyder/plugins/tests/` directory. In order that pytest can find your tests, the test file should have a name starting with `test` and the name of the test functions should also start with `test`.

For more details, look at the documentation of [pytest](http://pytest.org/latest/) and [pytest-qt](https://pypi.python.org/pypi/pytest-qt). The existing tests may also serve as inspiration.