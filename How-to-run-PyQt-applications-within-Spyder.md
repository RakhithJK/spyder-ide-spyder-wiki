**Important Note**: Before running a PyQt application in Spyder, you need to change your Graphics backend to `Automatic`. You can do that by going to

    Tools > Preferences > IPython Console > Graphics

After that, please restart your console kernels or Spyder itself for this change to take effect.

### Example PyQt applications that run in Spyder

These applications are based on this [code](https://pythonprogramminglanguage.com/pyqt5-hello-world/))

#### PyQt5
```python
import sys
from PyQt5 import QtCore, QtWidgets
from PyQt5.QtWidgets import QMainWindow, QLabel, QGridLayout, QWidget
from PyQt5.QtCore import QSize    
     
class HelloWindow(QMainWindow):
    def __init__(self):
        QMainWindow.__init__(self)
 
        self.setMinimumSize(QSize(100, 100))    
        self.setWindowTitle("Hello world") 
        
        centralWidget = QWidget(self)          
        self.setCentralWidget(centralWidget)   
 
        gridLayout = QGridLayout(self)     
        centralWidget.setLayout(gridLayout)  
 
        title = QLabel("Hello World from PyQt", self) 
        title.setAlignment(QtCore.Qt.AlignCenter)
        gridLayout.addWidget(title, 0, 0)
        
        menu = self.menuBar().addMenu('Action for quit')
        action = menu.addAction('Quit')
        action.triggered.connect(QtWidgets.QApplication.quit)
 
if __name__ == "__main__":
    def run_app():
        app = QtWidgets.QApplication(sys.argv)
        mainWin = HelloWindow()
        mainWin.show()
        app.exec_()
    run_app()

```

#### PyQt4

```python
import sys
from PyQt4 import QtCore
from PyQt4.QtGui import QMainWindow, QLabel, QGridLayout, QWidget, QApplication
from PyQt4.QtCore import QSize    
     
class HelloWindow(QMainWindow):
    def __init__(self):
        QMainWindow.__init__(self)
 
        self.setMinimumSize(QSize(100, 100))    
        self.setWindowTitle("Hello world") 
        
        centralWidget = QWidget(self)          
        self.setCentralWidget(centralWidget)   
 
        gridLayout = QGridLayout(self)     
        centralWidget.setLayout(gridLayout)  
 
        title = QLabel("Hello World from PyQt", self) 
        title.setAlignment(QtCore.Qt.AlignCenter)
        gridLayout.addWidget(title, 0, 0)
        
        menu = self.menuBar().addMenu('Action for quit')
        action = menu.addAction('Quit')
        action.triggered.connect(QApplication.quit)
 
if __name__ == "__main__":
    def run_app():
        app = QApplication(sys.argv)
        mainWin = HelloWindow()
        mainWin.show()
        app.exec_()
    run_app()
```

### An explanation

The most common problem when running a PyQt multiple times inside Spyder is that a QApplication instance remains in the namespace of the IPython console kernel after the first run. In other words, when you try to re-run your application, you already have a QApplication instance initialized.

Trying to remove that instance will probably cause your program to get stuck in a blocking while-loop, as suggested [here](https://stackoverflow.com/a/38285497), and using `sys.exit()` doesn't help since it's the same as trying to exit Python (and hence the IPython console).

In the code above you can see that we make a function for the creation of the QApplication instance (to make it local and prevent it to get into the namespace of the kernel). Another approach that could work in some cases is adding a validation for a QApplication instance with the method `instance()`. In the later case you will probably need to structure the `main` that creates the QApplication instance with something like this:

```python
 if not QApplication.instance():
        app = QApplication(sys.argv)
    else:
        app = QApplication.instance() 
``` 

### Useful info/issues/documentation of QApplication

* [Segmentation faults for multiple instances of QApplication](https://stackoverflow.com/questions/29451285/loading-a-pyqt-application-multiple-times-cause-segmentation-fault)
* [Single instance QApplication](http://doc.qt.io/qt-5/qapplication.html#QApplication)