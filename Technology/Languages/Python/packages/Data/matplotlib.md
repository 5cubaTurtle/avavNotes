## pyplot
using pyplot:
```python
import matplotlib.pyplot as plt
import numpy as np

def sig(x, base, max, width):
    return (max - base) / (1 + np.exp(- width * x)) + base

x_is = np.arange(-10, 10)
y_is = sig(x_is, base=0, max=4000, width=1)
plt.plot(x_is, y_is)
>>> Out[7]: [<matplotlib.lines.Line2D at 0x7f23f53e2760>]
plt.show()
```
