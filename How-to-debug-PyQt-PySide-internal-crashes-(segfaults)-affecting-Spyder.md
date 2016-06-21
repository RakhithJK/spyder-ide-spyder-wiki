# Introduction

Spyder is written in pure Python, so users should not be victims of severe crashes. Of course the application may freeze if an unknown bug leads to an infinite loop in the Python code. Sometimes, an unknown bug could also lead a feature to fail silently, leaving a traceback in Spyder's internal console. When debugging Spyder, this traceback is very precious as it often tells explicitely to the developers where the problem is.

However, sometimes the whole application may crash and terminate: this is called a segmentation fault (segfault) on Unix operating systems and this is due to the fact that graphical user interfaces of Spyder are handled by PyQt (or PySide), the Python bindings for Qt. Unfortunately, a segfault is harder to debug than a simple Python traceback.

# Linux

Debugging PyQt (or PySide) will require the installation of the debug versions of Python and PyQt (or PySide).

You may use one of the two following approaches:

1. **Analyze core dump with gdb**

    Open a terminal (assumes that Spyder is installed in ~/spyderlib:

    * you may have to enable core dumps: ulimit -c unlimited
    * then let's change the working directory: cd ~/spyderlib/spyderlib
    * run Spyder: python spyder.py
    * when Spyder crashes, a file named 'core' will be created in the current working directory
    * to start debugging, run gdb: gdb python core
    * in gdb:
        * show the backtrace: bt
        * show the list of threads: info threads 

2. **Run gdb from the start**

    Open a terminal (assumes that Spyder is installed in ~/spyderlib:

        then let's change the working directory: cd ~/spyderlib/spyderlib
        run Spyder inside gdb:
            gdb python spyder.py
            run
            when Spyder crashes, start debugging:
                show the backtrace: bt
                show the list of threads: info threads 
    
If you're running Spyder from source checkout, it is convenient to start Spyder with gdb through the bootstrap script:

    gdb -ex r --args python bootstrap.py --help

More details on debugging Python with gdb: http://wiki.python.org/moin/DebuggingWithGdb

# Windows

Debugging PyQt will require the installation of the debug versions of Python and PyQt. On Windows platforms, this means that you will have to build Python itself in debug mode, then PyQt in debug mode (with Visual C++ -- e.g. the free "Express" edition). This should be sufficient to provide all necessary symbols for debugging a severe crash. 