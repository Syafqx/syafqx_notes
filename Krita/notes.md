# Krita notes

## General notes
Create a new workspace and follow the layout on the snapshot. You can find more window inside `Settings > Dockers`, like the overview, and etc.

Shortcut need to be assign
* Freehand tool (lasso) to `L`
* Deselect to `ctrl+D`

---
Add `InvertMiddleClickZoom=true` line inside kritarc to invert the drag zoom. Don't place it at the end of the file, put in in the middle instead. You can follow the alphabetical order, maybe put it between this

```
...
GamutMasks.viewMode=0
InvertMiddleClickZoom=true      <-- Here for example
KineticScrollingEnabled=true
...
```

---
As for the nagivagation, the tablet keybind config does it all.


---
### Remove filename tab on canvas-only mode
This is the [link](https://krita-artists.org/t/remove-file-name-tab-from-canvas-only-mode/15364) to the forum, the script is on the comment further down.

Here's the comment itself in case if the discussion were to be deleted:

> How to Use:  
Copy & paste scripts to correct files, Start Krita and enable full_screen_tab_bar_remover_plugin from Kritas python plugins, restart Krita and tab bar should be removed from canvas only mode.

**File Tree**:
```
pykrita/
    full_screen_tab_bar_remover_plugin/
        __init__.py
    full_screen_tab_bar_remover_plugin.desktop
```
`full_screen_tab_bar_remover_plugin/__init__.py`:
```python
from krita import Krita, Extension
from PyQt5.QtCore import Qt, QObject, QEvent
from PyQt5.QtWidgets import QMdiArea, QTabBar

class FullScreenTabBarRemoverExtension(Extension):
    def setup(self):
        pass

    def createActions(self, window):
        window.qwindow().installEventFilter(self)

    def eventFilter(self, qwin, event):
        if (event.type() == QEvent.WindowStateChange):
            is_full_screen = bool(qwin.windowState() & Qt.WindowFullScreen)
            mdi_area = qwin.centralWidget().findChild(
                    QMdiArea, None, Qt.FindDirectChildrenOnly)
            if mdi_area is not None:
                tab_bar = mdi_area.findChild(
                        QTabBar, None, Qt.FindDirectChildrenOnly)
                if tab_bar is not None:
                    for i in range(tab_bar.count()):
                        tab_bar.setTabVisible(i, not is_full_screen)
                    mdi_area.setViewportMargins(0, 0, 0, 0)
        return super().eventFilter(qwin, event)

app = Krita.instance()
app.addExtension(FullScreenTabBarRemoverExtension(app))
```
*.desktop is for linux only.*  
`full_screen_tab_bar_remover_plugin.desktop`:
```
[Desktop Entry]
Type=Service
ServiceTypes=Krita/PythonPlugin
X-KDE-Library=full_screen_tab_bar_remover_plugin
X-Python-2-Compatible=false
X-Krita-Manual=readme.md
Name=Full Screen Tab Bar Remover Plugin
Comment=Hides tab bar for full screen canvas.
```

## External link
* [Sketch V2 brushes](https://krita-artists.org/t/sketch-v2-sk2-pleasure-to-draw-including-colored-pencils-and-blenders/59552)
* [Hard Brushes pack](https://krita-artists.org/t/hard-brushes-pack/92704)