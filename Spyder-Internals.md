This section aims to give an introduction into Spyder internals.

**Note: This is a work in progress!**

# Directory Structure

The following tree represents the current structure of Spyder master repo. The branches here represent only folders, more specifics and explanations will be given below.

├── [spyder-ide/spyder.git](https://github.com/spyder-ide/spyder) <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [[#app_example]]                     <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [[#doc]]                             <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── external-py2
&nbsp;&nbsp;&nbsp;&nbsp;├── external-py3
&nbsp;&nbsp;&nbsp;&nbsp;├── img_src
&nbsp;&nbsp;&nbsp;&nbsp;├── rope_profiling
&nbsp;&nbsp;&nbsp;&nbsp;├── scripts
&nbsp;&nbsp;&nbsp;&nbsp;├── spyderlib
&nbsp;&nbsp;&nbsp;&nbsp;│   ├── defaults             // 
&nbsp;&nbsp;&nbsp;&nbsp;│   ├── images               // 
&nbsp;&nbsp;&nbsp;&nbsp;│   ├── locale               // 
&nbsp;&nbsp;&nbsp;&nbsp;│   ├── plugins              // 
&nbsp;&nbsp;&nbsp;&nbsp;│   ├── qt                   // 
&nbsp;&nbsp;&nbsp;&nbsp;│   ├── utils                // 
&nbsp;&nbsp;&nbsp;&nbsp;│   ├── widgets              // 
&nbsp;&nbsp;&nbsp;&nbsp;│   │   ├── externalshell    // 
&nbsp;&nbsp;&nbsp;&nbsp;│   │   └── sourcecode       // 
&nbsp;&nbsp;&nbsp;&nbsp;│   └── windows              // 
&nbsp;&nbsp;&nbsp;&nbsp;└── [[#spyderplugins]]

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


