#python 
[Real Python](https://realpython.com/python-traceback/)
print trace-back of exception: 
```python
import traceback
except Exception as e:
	traceback.print_exc()
    print(f"exception caught {repr(e)[:10]}")
```
