| key            | value                                                 |
|----------------|-------------------------------------------------------|
| Status         | Active                                                |
| Author         | anatoly techtonik &lt;techtonik@gmail.com&gt; / [@techtonik](https://github.com/techtonik)   |
| Created        | April 15, 2015                                        |
| Updated        | April 15, 2015                                        |
| Discussion     | -PR TBD-     |
| Implementation | -PR TBD-                                        |


Generic plugin subsystem for Spydey is a set of conventions that can be reused outside of Spyder. This means that plugin can adapt itself to different tools and chooses provided dependencies and feature depending on environment where it is run.

To allow max adoption, the Spydey GPS core (the tricky part on application side) should be released as CC0 / Public domain / Unlicense.

# TL;DR

    def init(spyenv):
      pass

`spyenv` is any object that allows plugin to inspect it.

# Plugin decoupling and delayed imports

    def init(spyenv):
      if not hasattr(spyenv, 'appname'):
        return
      if spyenv.appname != 'spyder':
        return
      imports()
      return True

    def imports():
      global spy
      import spy

To avoid dependency on Spyder, there should not be any non-standard imports on global level. So the plugin encapsulates all the checks inside `init()` method and does imports only when everything else is ok.

Plugin should not import anything except base Python dependencies at its top level or `init()` to allow application inspect plugins that are conflicting (like choose the best version of the same plugin).

# Formal specification

Specification or speccy is divided into levels. Every new level restricts flexibility and makes the protocol between plugin and application more strict / defined. You're free to implement the speccy until any level and state that in your plugin docs.

Every new level should solve a real issue and follow at least one of the following principles:

 - make plugin code less mystic
 - make plugin code less verbose
 - make plugin writing a less repeatable process
 - anything that improves usability and experience of plugin maintainers

## Level 0

1. Plugin provides init(spyenv) method
2. App calls init() method with object

The return value for init() method is not defined at this level of speccy. The required structure of spyenv object depends on application needs and is also not defined by ground zero.

