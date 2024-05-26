getting the hostname:
Option 1: Using the `socket` module
```python
import socket
hostname = socket.gethostname()
```

Option 2: Using the `platform` module
```python
import platform
hostname = platform.node()
```

Option 3: Using the `os` module
```python
import os
hostname = os.uname().nodename
```

Option 4: Using the `sys` package:
```python
import sys
hostname = sys. gethostname()
```