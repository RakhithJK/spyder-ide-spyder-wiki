For general information about plugins, see https://github.com/spyder-ide/spyder/wiki/User-plugins

For creating new plugins you could use [spyder-plugin-cookiecutter](https://github.com/spyder-ide/spyder-plugin-cookiecutter/)


# UI plugins

These third-party plugins may communicate with other Spyder components through the plugin interface (see https://github.com/spyder-ide/spyder/blob/master/spyder/api/plugins.py).

```
spyder_<PLUGIN_NAME>
├── __init__.py
├── <PLUGIN_NAME>plugin.py
├── tests/
│   ├── __init__.py
│   └── test_plugin.py
├── utils/
│   └── __init__.py
├── assets/
├── locale/   # Translations
└── widgets/
    ├── __init__.py
    ├── <PLUGIN_NAME>gui.py
    └── tests
        ├── __init__.py
        └── test_report_widget.py
```

# I/O Spyder plugins

How to create your own I/O Spyder plugins:

   * Create a Python module named `spyder_io_foobar` where `foobar` is the name of your plugin
   * Write your loading function and/or your saving function:
       * `load`:
           * input is a string: `filename`
           * output is a tuple with two elements: dictionary containing at least one element (key is the variable name) and error message (or None) 
       * `save`:
           * `input` is a tuple with two elements: `data` (dictionary), `filename`
           * `output` is a string or `None`: error message or `None` if no error occured 
   * Define the global variables `FORMAT_NAME`, `FORMAT_EXT`, `FORMAT_LOAD` and `FORMAT_SAVE`. See the example of DICOM images support:

       * https://github.com/spyder-ide/spyder/tree/master/spyder_io_dcm

   * More examples of load/save functions may be found here:

       * https://github.com/spyder-ide/spyder/blob/master/spyder/utils/iofuncs.py