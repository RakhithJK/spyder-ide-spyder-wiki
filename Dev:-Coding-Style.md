**Note: This is a work in progress!**

# Coding style

Please follow these coding standards when writing code for inclusion in Spyder.

## Python style

Unless otherwise specified, follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) specifications and recommendations for coding style and [PEP 257](https://www.python.org/dev/peps/pep-0257/) for docstrings.

Use flake8 to check for problems in this area. Remember that PEP 8 is only a guide, so respect the style of the surrounding code as a primary goal.

Additional conventions:

* Always use four (4) spaces for **indentation**, including continuation lines and hanging indents, except for:
* Use 8 spaces for hanging indent continuations of the ``def``, ``if``, ``for``, ``while`` and ``with`` statements, to avoid confusion with their indented block
* **Test-suite functions** need not have a separate summary line in the docstring, particularly if it is only a few lines long, though this is suggested for longer docstrings
* Put the ``"""`` on their own lines for multi-line **docstrings**; keep them all in the same line for single-line docstrings, except for module-level docstrings
* **Commit messages and code comments** should be in imperative tense ("do this", "fix that"), sufficiently descriptive of the subject matter, understandable by themselves, and avoid non-obvious abbreviations or acronyms. Commit messages and **issue/PR titles** should not have a period. Prefix all PR titles with ``PR: `` and Work in progress PRs with ``[WiP]``.


## PyQt / PySide Style
Spyder aims to be compatible with PySide and PyQt, so make sure code runs with both bindings.

Qt by default has its own conventions for the definitions of methods and classes, and sometimes this clashes with was is suggested by [PEP 8](https://www.python.org/dev/peps/pep-0008/). 

These are some suggestions to take into account when using the Qt bindings in Python:

### Method naming conventions
Qt defines methods in camelCase, and when Spyder overloads these methods, we cannot avoid camelCase. However, When new methods are defined in Spyder, these methods should follow the PEP8 convention:

```python
class SpyderWidget(QWidget):
    """Example widget."""
    def __init__(self, parent):
        QWidget.__init__(self, parent)
   
    def mousePressEvent(self, event):
        """Overloaded Qt method."""
        # Do something with the event...

    def run_new_method(self):
        """Run some new method."""
        # Do something interesting
```

### Widget Structure
Most Spyder widgets follow this convention (use it when creating new widgets)


```
# Variables

# Widgets

# Widget setup

# Layouts

# Signals and slots
```
Example:

```python

class SomeWidget():
    # Variables
    self.some_variable = None
  
    # Widgets
    self.super_widget = SomeSuperWidget()

    # Widget setup
    self.super_widget.setSomething(True)

    # Layouts
    layout = QVBoxLayout()
    layout.addWidget(self.super_widget)
    self.setLayout(layout)

   # Signals and slots
   self.super_widget.sig_some_signal.connect(self.some_other_method)
```

### Docstrings
Docstrings are sentences in the infinitive form and ended with a dot `.`. The `__init__` share (at least) the same docstring as the class.

Example:

```python

class SomeWidget():
    """Create some widget."""

    def __init__(self):
        """Create some widget."""
```


### Imports
TODO:

## Spyder style

### Internationalization / Localization
TODO:

```python
from spyderlib.baseconfig import _

```


### Signals
- When working with signals, use the [new style](http://pyqt.sourceforge.net/Docs/PyQt4/new_style_signals_slots.html):
- For naming new custom signals, use the `sig_` prefix
    ```python
    from spyderlib.qt.QtCore import Signal
    
    class SpyderWidget(SpyderPluginWidget):
        """Multi-file Editor widget"""    

        # Signals
        sig_run_in_current_ipyclient = Signal(str, str, str, bool, bool)
    
    ```