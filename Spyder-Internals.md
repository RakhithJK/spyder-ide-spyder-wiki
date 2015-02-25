This section aims to give an introduction into Spyder internals.

# Directory Structure

The following tree represents the current structure of Spyder master repo. The branches here represent only folders, more specifics and explanations will be given below.

    ├── app_example
    ├── doc
    ├── external-py2
    ├── external-py3
    ├── img_src
    ├── rope_profiling
    ├── scripts
    ├── spyderlib
    │   ├── defaults             // 
    │   ├── images               // 
    │   ├── locale               // 
    │   ├── plugins              // 
    │   ├── qt                   // 
    │   ├── utils                // 
    │   ├── widgets              // 
    │   │   ├── externalshell    // 
    │   │   └── sourcecode       // 
    │   └── windows              // 
    └── spyderplugins

## doc
As the name suggests this is the folder where the documentation of the project resides. 
The documentation is written in [reStructuredText](http://docutils.sourceforge.net/rst.html) (.rst) and is parsed using [Sphinx]().

## external-py2

## external-py3

## img_src
TODO:

## rope_profiling
TODO:

## scripts
TODO:

## spyderlib
This is the actual main module of Spyder. 
The name spyderlib is due to the existence of another project with the spyder name.


### locale 
TODO: 

### plugins
TODO:

### qt
TODO:

### widgets
TODO:

#### externalshell
TODO:

#### sourcecode
TODO:

### spyderplugins
TODO:


**Note: This is a work in progress!**