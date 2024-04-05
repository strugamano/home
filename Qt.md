# Qt snippets

## basic setup

```python
import sys
from PySide6 import QtWidgets
from PySide6.QtCore import Slot
from ui.MainWindow import Ui_MainWindow  # Qt Designer UI files in /ui


class MainWindow(QtWidgets.QMainWindow, Ui_MainWindow):
    def __init__(self):
        super(MainWindow, self).__init__()

        self.setupUi(self)

        # [...]

    # SLOTS

    @Slot()
    # def slot_action() [...]


app = QtWidgets.QApplication(sys.argv)

window = MainWindow()
window.show()
app.exec()
```

## toolbar

```python
import sys
from PySide6 import QtWidgets
from PySide6.QtCore import Slot
from PySide6.QtGui import QAction, QIcon


# main window class
    # init

        spacer = QtWidgets.QWidget()  # spacer for widgets
        spacer.setSizePolicy(QtWidgets.QSizePolicy.Expanding, QtWidgets.QSizePolicy.Expanding)

        # ----- TOOLBAR -----

        # CONFIG
        about_action = QAction(QIcon('ui/configure.svg'), "Configuration", self)
        # config_action.triggered.connect(self.config_action)
        self.toolbar.addAction(about_action)

        # <--- left side
        self.toolbar.addWidget(spacer)
        # right side --->

        # ABOUT
        about_action = QAction(QIcon('ui/help-about.svg'), "About", self)
        about_action.triggered.connect(self.about_action)
        self.toolbar.addAction(about_action)

        # EXIT
        exit_action = QAction(QIcon('ui/window-close.svg'), "Exit", self)
        exit_action.triggered.connect(self.exit_action)
        self.toolbar.addAction(exit_action)

    @Slot()  # exit
    def exit_action(self): sys.exit('Goodbye!')

    @Slot()   # about
    def about_action(self): print('About...')

```
