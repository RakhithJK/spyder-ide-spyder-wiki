# Shortcuts

With some recents changes on the 4.x branch, to correctly display shortcuts in the preferences table 
you need to make sure that shortcuts are registered correctly by the plugin.

The plugin must register the widget shortcuts of any widget that exposes shortcuts and must also register plugin shortcuts (see `get_plugin_actions` method).

Example

```python
# Widget file
class ThirdPartySubWidget(QWidget):

    def __init__(self, parent=None):
        self.shortcuts = self.create_shortcuts()

    def some_method_call(self):
        pass

    # Needed!
    def create_shortcuts(self):
        some_other_shortcut = CONF.config_shortcut(
            lambda: self.some_method_call(),
            context='terminal',
            name='some other shortcut',
            parent=self,
        )
        return [some_other_shortcut]

    # Needed!
    def get_shortcut_data(self):
        return [sc.data for sc in self.shortcuts]


# Plugin file
class ThirdPartyPlugin(SpyderPluginWidget):

    def __init__(self, parent=None):
         self.a_sub_widget = ThirdPartySubWidget(self)
         self.register_widget_shortcuts(self.a_sub_widget)

    def get_plugin_actions(self):
        some_action = create_action(
            self,
            _("Some action text"),
            tip=_("Some action tip"),
            icon=ima.icon('some-icon'),
            triggered=self.quit,
        )
        # The CONF must contain a shortcut  `_/quit` in the shortcuts section
        self.register_shortcut(some_action, context="_", name="Quit")

        return [some_action]
```

