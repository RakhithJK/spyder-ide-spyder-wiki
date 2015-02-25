This section aims to give an introduction into Spyder internals.

**Note: This is a work in progress!**

# Directory Structure

The following tree represents the current structure of Spyder master repo. The branches here represent only folders, more specifics and explanations will be given below.


:open_file_folder: [spyder-ide/spyder.git](https://github.com/spyder-ide/spyder)       <br>
├── [app_example](#app_example)                                                        <br>
├── [doc](#doc)                                                                        <br>
├── [external-py2](#external-py2)                                                      <br>
├── [external-py3](external-py3)                                                       <br>
├── [img_src](#img_src)                                                                <br>
├── [rope_profiling](#rope_profiling)                                                  <br>
├── [scripts](#scripts)                                                                <br>
├── [spyderlib](#spyderlib)                                                            <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [defaults](#defaults)                                     <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [images](#images)                                         <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [locale](#locale)                                         <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [plugins](#plugins)                                       <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [qt](#qt)                                                 <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [utils](#utils)                                           <br>
│&nbsp;&nbsp;&nbsp;&nbsp;├── [widgets](#widgets)                                       <br>
│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;├── [externalshell](#externalshell)  <br>
│&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;└── [sourcecode](#sourcecode)        <br>
│&nbsp;&nbsp;&nbsp;&nbsp;└── [windows](#windows)                                       <br>
└── [spyderplugins](#spyderplugins)<br>

## app_example
TODO:

## doc
As the name suggests this is the folder where the documentation of the project resides. 
The documentation is written in [reStructuredText](http://docutils.sourceforge.net/rst.html) (.rst) and is parsed using [Sphinx](http://sphinx-doc.org/).

## external-py2
TODO:

## external-py3
TODO:

## img_src
TODO:

## rope_profiling
TODO:

## scripts
TODO:

## spyderlib
This is the actual main module of Spyder. 
The name spyderlib is due to the existence of another project with the spyder 

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
