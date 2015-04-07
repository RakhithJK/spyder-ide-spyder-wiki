| key            | value                                                 |
|----------------|-------------------------------------------------------|
| Status         | Active                                                |
| Author         | Gonzalo Peña-Castellanos / (@goanpeca)                |
| Created        | April, 2015                                           |
| Updated        | April, 2015                                           |
| Discussion     | link to the issue where the SEP is being discussed    |
| Implementation | link to the PR                                        |

# Rationale
To have a clean separation of public api (for plugin development and users) and private api (for spyder development and contributors). 

This would allow to decouple internal and public api, and get (at the expense of some extra classes...) a clean separation. We can also implement counters in the public API.

# Example

```python
# spyder_widget_example.py


class SpyderWidgetAPI:
    def __init__(self, widget, plugin):
        self.widget = widget
        self.plugin = plugin

    # Stable API available to the public / plugin developers
    def public_api_method_1(self):
        # Calls to private api (only, so no `_`, or `__` methods)
        self.widget.private_api_method_1()

    def public_api_method_2(self):
        # Calls to private api (only, so no `_`, or `__` methods)
        ....

class SpyderWidget:
    def __init__(self, plugin):
        self.api = SpyderWidgetAPI(self, plugin)
        ....

    # Not necessarily stable API available to core developers of Spyder
    def private_api_method_1(self):
        # Calls to private api or more private methods of super private methods
        # A method to be called from anywhere in spyder

    def _private_method_1(self):
        # Calls to private api or private methods of super private methods
        # A method to be called from anywhere within this spyder module

    def __super_private_method_1(self):
        # Calls to private api or private methods of super private methods
        # A method to be called from within this SpyderWidget class only
```

Which from the internal console would be called something like....

`spy.window.editor.api.public_method_1()`

Or even create a module to handle all this api in a single place (call, import) so we could have.

```python

from spyder.api import variabe_explorer

variabe_explorer.public_api_method_1()
...
```

Where `spyder.api` module would import all the available api's in spyder
