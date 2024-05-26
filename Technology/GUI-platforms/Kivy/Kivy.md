#python #GUI #NUI
Links: [wiki](https://en.wikipedia.org/wiki/Kivy_(framework)), [docs](https://kivy.org/doc/stable/)

## Classes
### App
Hello World App:
```python
from kivy.app import App
from kivy.uix.label import Label

class MainApp(App):
    def build(self):
        return Label(text="Hello, World!")

MainApp().run()
```
#### build()
`build()` method is the entry point to whatever will be drawn on the screen.