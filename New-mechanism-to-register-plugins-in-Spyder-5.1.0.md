Spyder **5.1.0** comes with an important, breaking change to our API. The `register` method of the `SpyderPluginV2` API was replaced by `on_initialize`. In that method you need to write all code necessary to initialize the plugin on its own (instantiating its own classes, connecting Qt signals, etc).

If your plugin requires others to work, you need to import the `on_plugin_available` decorator from `spyder.api.plugin_registration.decorators`, and use it to decorate a method that will use the other plugin API to perform certain actions.

For instance, let's say you emit a signal in your container that needs to do something at the plugin level, and you created an action that needs to be registered in one of our menus. In Spyder 5.1.0 the code to do that will look like this

```python
from spyder.api.plugin_registration.decorators import on_plugin_available
from spyder.api.plugins import Plugins, SpyderPluginV2
from spyder.plugins.mainmenu.api import ApplicationMenus


def MyPlugin(SpyderPluginV2):

    REQUIRES = [Plugins.MainMenu]

    def on_initialize(self):
        container = self.get_container()
        container.sig_do_something_requested.connect(self.on_do_something)

    @on_plugin_available(plugin=Plugins.MainMenu)
    def on_main_menu_available(self):
        """"Register my_action in Tools menu."""
        container = self.get_container()
        main_menu = self.get_plugin(Plugins.MainMenu)

        main_menu.add_item_to_application_menu(
            container.my_action,
            menu_id=ApplicationMenus.Tools,
        )

    def on_do_something(self):
        """Print a simple message."""
        print("Let's do something!")
```