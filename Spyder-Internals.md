This section aims to give an introduction into Spyder internals.

**Note: This is a work in progress!**

# Directory Structure

The following tree represents the current structure of Spyder master repo. The branches here represent only folders, more specifics and explanations will be given below.


├── [spyder-ide/spyder.git](https://github.com/spyder-ide/spyder) <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [app_example](#app_example)           <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [doc](#doc)                              <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [external-py2](#external-py2)                           <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [external-py3](external-py3)                        <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [img_src](#img_src)                                   <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [rope_profiling](#rope_profiling)                             <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [scripts](#scripts)                                      <br>
&nbsp;&nbsp;&nbsp;&nbsp;├── [spyderlib](#spyderlib)                                       <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [defaults             // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [images               // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [locale               // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [plugins              // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [qt                   // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [utils                // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [widgets              // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [externalshell // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;└── [sourcecode     // <br>
&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;└── windows              // <br>
&nbsp;&nbsp;&nbsp;&nbsp;└── [spyderplugins](#spyderplugins)<br>

## app_example

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


