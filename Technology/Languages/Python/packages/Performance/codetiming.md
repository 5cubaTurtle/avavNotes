#python #time 
Timer class
[Real Python](https://realpython.com/python-timer/), [github](https://github.com/realpython/codetiming)

### Usage:
As [[contex-manager]]:
```python
from codetiming import Timer
with Timer(name='angle_calc', text="{name}:{:.9f} Sec", logger=logger.debug):
	# do something you want to time
```

As a class:
```python
t = Timer(name="class")
t.start()
# Do something
t.stop()
```

As a [[Learn-Decorators|Decorator]]:
```python
@Timer(name="decorator")
def stuff():
    # Do something
```

### Arguments
`Timer` accepts the following arguments when it's created. All arguments are optional:
-   **`name`:** An optional name for your timer
-   **`text`:** The text that's shown when your timer ends. It should contain a `{}` placeholder that will be filled by the elapsed time in seconds (default: `"Elapsed time: {:.4f} seconds"`)
-   **`initial_text`:** Show text when your timer starts. You may provide the string to be logged or `True` to show the default text `"Timer {name} started"` (default: `False`)
-   **`logger`:** A function/callable that takes a string argument and will report the elapsed time when the logger is stopped (default: `print()`)
You can turn off explicit reporting of the elapsed time by setting `logger=None`.
In the template text, you can also use explicit attributes to refer to the `name` of the timer or log the elapsed time in `milliseconds`, `seconds` (the default), or `minutes`.
For example:
```python
t1 = Timer(name="NamedTimer", text="{name}: {minutes:.1f} minutes")
t2 = Timer(text="Elapsed time: {milliseconds:.0f} ms")
```

### Named Timers
Named timers are made available in the class dictionary `Timer.timers`. The elapsed time will accumulate if the same name or same timer is used several times.
You can also get simple statistics about your named timers. Continuing from the example above:
```python
>>> Timer.timers.max("example")
3.5836678670002584

>>> Timer.timers.mean("example")
2.6563487200000964

>>> Timer.timers.stdev("example")
1.311427314335879
```
`timers` support `.count()`, `.total()`, `.min()`, `.max()`, `.mean()`, `.median()`, and `.stdev()`.
