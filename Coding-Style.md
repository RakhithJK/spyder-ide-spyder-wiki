*Adapted from https://docs.djangoproject.com/en/1.7/internals/contributing/writing-code/coding-style/*

# Coding style

Please follow these coding standards when writing code for inclusion in Spyder.

# Python style

Unless otherwise specified, follow [PEP 8](https://www.python.org/dev/peps/pep-0008/).

Use flake8 to check for problems in this area. Remember that PEP 8 is only a guide, so respect the style of the surrounding code as a primary goal.

One big exception to PEP 8 is our preference of longer line lengths. We’re well into the 21st Century, and we have high-resolution computer screens that can fit way more than 79 characters on a screen. Don’t limit lines of code to 79 characters if it means the code looks significantly uglier or is harder to read.

* Use four spaces for indentation.

# PyQt / PySide Style
Qt by default has its own conventions for the definitions of methods and classes, and sometimes this clashes with was is suggested by [PEP 8](https://www.python.org/dev/peps/pep-0008/). 

These are some suggestions to take into account when using the Qt bindings in Python:

* Qt defines methods in camelCase, and when Spyder overloads these methods, we cannot avoid camelCase. However, When new methods are defined in Spyder, these methods should follow the PEP8 convention:

    ```python
class SpyderWidget(QWidget):
    """ Example widget """
    def __init__(self, parent):
        QWidget.__init__(self, parent)
    
    def mousePressEvent(self, event):
        """ Overloaded method """
        # Do something with the event...

    def new_method(self):
        """ Some docstring """
        # Do something interesting
    ```

* **QUESTION:** Should we define some conventions as well for widgets? or for signal naming? for instance:
    - When working with signals, use the new style:
    - For naming custom signals, use the `sig_` prefix?:
    ```python
    class SpyderWidget(SpyderPluginWidget):
        """
        Multi-file Editor widget
        """    
        # Signals
        sig_run_in_current_ipyclient = Signal(str, str, str, bool, bool)
    
    ```

# Internationalization / Localization
TODO:

```python
from spyderlib.baseconfig import _


```
