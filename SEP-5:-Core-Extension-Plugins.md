| key            | value                                                 |
|----------------|-------------------------------------------------------|
| Status         | Active                                                |
| Author         | Full Name &lt;full.name@gmail.com&gt;                 |
| Created        | February, 2015                                        |
| Updated        | February, 2015                                        |
| Discussion     | link to the issue where the SEP is being discussed    |
| Implementation | link to the PR                                        |

**Note: Work under progress**

# Description 
Spyder was born as an IDE built using Python for use with the Python language. With more and more enhancements and the appearance of new dedicated libraries, frameworks and languages, Scientific Research and Computing is no longer tied exclusively to Python scripts (well it never was like this...). 

New needs involved in scientific computing include:
* Using Python web frameworks:
    - Django
    - Flask?
* Using Python Static site generators:
    - Pelican
* Using Python Documentation generators:
    - Sphinx
    - Mkdocs
* Using other languages to complement/experiment/explore
    - Julia
    - C
    - R

As the list grows and grows it seems unfeasible and unrealistic to provide support from the core of Spyder to all these different frameworks/languages/Projects. 

# Current status
The current plugin interface allows for the creation of new widgets/panels to provide new functionality (Profiler, Pylint, Conda Packages etc...), but there is no clear and defined way of extending the functionality of core Spyder plugins (Variable Explorer, Editor, Object Inspector, Consoles).

# Proposal
Describe a set of methods/signals and objects (menu, toolbars, Widgets/Panel) that would constitute a public API to extend connect from installable external plugins.

## Toolbars

## Menus

### Menu: Run

## Widgets/Panels

### Widget: Editor

### Widget: Variable Explorer


**Note: Work under progress**

I have some ideas but we need to figure out how these plugins (the installable ones I mean) should be incorporated. Should each dockwidget plugin has some machinery to look for plugins that extend its functionality? or should Spyder as a final step of setup go through all installed plugins and modify the core dockwidget plugins accordingly (depending if the plugin is enable or not)?

*--- side note: the name plugins brings confusion, "Editor Plugin" is a core dockwidget, but we have also plugins to be installed eventually, but these words do not relate to each other ---*

The first thing I think of changing with how it is currently set is, get rid of the `is_python` method in the sourcecode editor and replace it for a more global way (language agnostic) to get the filetype or the language and from that language a dictionary could hold all relevant actions for the language (for instance in the run menu). When a plugin is installed it could add actions to this dictionary (part of the public API) so that when the run menu is rendered it would adjust the actions (instead of graying them out), so if a markdown fie is open, only a `Parse` action (`F5`) would be seen instead of 7 grayed out actions. Instead if having a variable holding the RUN menu, we could have the variable hold a dictionary with base actions, and a set of actions defined for each language (that is added via a plugin)

A similar principle could hold for all the other menus, expect in menus that affect ALL types of files, the actions to add should be placed in a specific section only... as to not get an additional action below the `Quit` button in the File menu, which would make no sense!

To do this we should define some global constants to refer to the languages.... something  like:

```
spyder.constants.languages.PYTHON
spyder.constants.languages.MARKDOWN
spyder.constants.languages.UNDEFINED
```

The sourcecodeeditor should have then a method like...   `get_language` that would look if it is .md or .markdown... and return `spyder.constants.languages.MARKDOWN` or spyder.constants.languages.UNDEFINED, in which case no special actions should be added (much like what happens now with any language besides python)

With all in place, then we could look at the object inspector, which actually would not need much change as the way I see it would just accept some input from a function `render_this_html(self, html)` tied to the added Parse action in the run menu. Also this plugin would have `mistune` as a dependency, and maybe a version of the Editor and Object Inspector Public API. If we have a version for the API of each dockwidget it would be easier to control changes per dockwidget plugin and also have checks to ensure that an installable plugin can work.
