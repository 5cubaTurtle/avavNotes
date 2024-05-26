For list of signals see [[kill]]

catch a [[kill|signal]]:
```python
import signal
import sys

# Define a signal handler function
def signal_handler(sig, frame):
    print('You pressed Ctrl+C!')
    sys.exit(0)

# Set the signal handler for SIGINT
signal.signal(signal.SIGINT, signal_handler)

print('Press Ctrl+C to raise a SIGINT signal')
signal.pause()  # Wait for a signal
```

#### passing arguments to signal handler
it's not possible to pass arbitrary arguments to a signal handler directly because the handler function must have only two arguments: the signal number and the current stack frame (or `None` if unavailable).

However, there are some workarounds to pass arguments to a signal handler function. One way is to use a global variable:
```python
import signal

# Define a signal handler function
def signal_handler(sig, frame):
    print(f"You passed the value {value} to the handler")

# Set the signal handler for SIGINT
signal.signal(signal.SIGINT, signal_handler)

# Set the value to be passed to the signal handler
value = 42

# Wait for a SIGINT signal
print('Press Ctrl+C to raise a SIGINT signal')
signal.pause()
```
the `value` variable is set before the signal handler is registered. The handler function can then access this variable and use its value as needed.

Another way is to use the `functools.partial` function to create a new function with predefined arguments:
```python
import signal
import functools

# Define a signal handler function
def signal_handler(value, sig, frame):
    print(f"You passed the value {value} to the handler")

# Set the signal handler for SIGINT
signal.signal(signal.SIGINT, functools.partial(signal_handler, value=42))

# Wait for a SIGINT signal
print('Press Ctrl+C to raise a SIGINT signal')
signal.pause()
```
the `functools.partial` function is used to create a new function that calls `signal_handler` with the `value` argument set to `42`. This new function is then registered as the signal handler.

When the signal is received, the handler function is called with the `sig` and `frame` arguments, and the `value` argument is passed along with them.

Handlers should be kept as simple as possible and avoid doing any heavy computation or blocking I/O. In addition, it's generally a good practice to use global variables and `functools.partial` sparingly and only when necessary.


