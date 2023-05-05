# cdoe.editor
#editor-code-text
## Usage/Examples
```python 
from tkinter import *
import ctypes
import re
import os
```
```python 
ctypes.windll.shcore.SetProcessDpiAwareness(True)
root = Tk()
root.geometry('500x500')
def execute(event=None):
    with open('run.py', 'w', encoding='utf-8') as f:
        f.write(editArea.get('1.0', END))
    os.system('start cmd /K "python run.py"')
def changes(event=None):
    global previousText
    if editArea.get('1.0', END) == previousText:
        return
```
```python 
repl = [
    ['(^| )(False|None|True|and|as|assert|async|await|break|class|continue|def|del|elif|else|except|finally|for|from|global|if|import|in|is|lambda|nonlocal|not|or|pass|raise|return|try|while|with|yield)($| )', keywords],
    ['".*?"', string],
    ['\'.*?\'', string],
    ['#.*?$', comments],
]
editArea = Text(
    root,
    background=background,
    foreground=normal,
    insertbackground=normal,
    relief=FLAT,
    borderwidth=30,
    font=font
)
editArea.pack(
    fill=BOTH,
    expand=1
)
editArea.insert('1.0', """from tkinter import *
import ctypes
import re
import os
ctypes.windll.shcore.SetProcessDpiAwareness(True)
# Setup Tkinter
root = Tk()
""")
```

