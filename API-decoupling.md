# Description

This a quick summary of the intended language decoupling for spyder and the creation of a simplified api for third party plugins, where all base plugins are extendable.

# Languages
Languages and extensions are already defined in the config, this can be used as based, but moved to the spyder/api folder. Initially we should limit the number of languages offered but we could also create a register language method to make it more generic. This would allow for third party devs to register languages not provided by default?, do we need to offer the concept of a sublanguage (python-django, python-flask?) so that one language can offer different functionalities based on the sublanguage?

# Widgets
Every widget must be language agnostic that, so to use it and initialize it should receive information in a neutral representation (JSON?)

# Managers
All widgets in Spyder will have a corresponding Manager class in charge of providing the adequate behavior depending on the state of either the project, the current editor type or/and the current console type. This manager classes will be responsible for the registration of new behavior.

Managers do not need to be exposed in the api as the only function needed is the `register_<widget>`.
It can be located at

`spyder.api._managers.py`
or

`spyder.api.managers.py`

or inside each specific widget api

`spyder.api.<widget_name.py>`

# API


