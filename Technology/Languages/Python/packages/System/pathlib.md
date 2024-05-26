#python 

import: `from pathlib import Path`

create a Path object for a file *special_config*:
```python
special_config = Path('/home/robot/special_config')
```
check if file exists: `special_config.exists()`
create a file if not exists:  
```python
myfile = Path('myfile.txt')
myfile.touch(exist_ok=True)
```
- When the `exist_ok` parameter is set to True, the function will not take any action if the file is present.

add to a PosixPath another PosixPath and another folder (*str* type):
```python
model_temp = root / model_env / 'temp'
```

#### Correspondence to tools in the [`os`](https://docs.python.org/3/library/os.html#module-os "os: Miscellaneous operating system interfaces.") module [doc](https://docs.python.org/3/library/pathlib.html#correspondence-to-tools-in-the-os-module "Permalink to this headline")
basename: `myfile.name`
dirname: `myfile.parent`