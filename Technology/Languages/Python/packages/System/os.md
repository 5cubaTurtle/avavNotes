---
Invocation: import os
---
#python 

#### environment variables
get [[environment-variables|env variable]]:   `os.environ.get('ROBOT')`, or `get('ROBOT', default)` will return the `default`  which was provided in case `ROBOT` env variable is not defined.
set [[environment-variables|env variable]]:   `os.environ["LOG_TOOL_DEBUG"] = "1"`
expand variable: `os.path.expandvars('$ROBOT')` >> 'PLC2-0-005'

#### path
[doc](https://docs.python.org/3/library/os.path.html)
current folder (*str*): `os.getcwd()`
change current dir: `os.chdir('/path/to/new/directory')`
home dir: `os.path.expanduser('~')`
join path: `os.path.join("a/path/through", "a/folder", "to/some/file")` >>>
	*a/path/through/a/folder/to/some/file*
get the realpath of a file: `os.path.realpath(path/to/file)`
get the [[basename]] of a path(*str*): `os.path.basename(current_dir)`
get the directory of a path(*str*): `os.path.dirname(some_path)`
check if a file exists: `os.path.exists('/path/to/file')`
create [[soft-link]]: `os.symlink('/usr/local/bin/python3', 'python3-link')`
##### real vs absolute
Absolute path will return the [[soft-link|linked]] path while realpath will returned the canonical(the actual location of the file with no links in the path string) path
```python
os.symlink('/usr/local/bin/python3', 'python3-link') # Create a symbolic link
# Get the absolute path and canonical path of the symbolic link
abs_path = os.path.abspath('python3-link') # /path/to/current/folder/python3-link
real_path = os.path.realpath('python3-link') # /usr/local/bin/python3
```

#### Directories
List all files of a directory: `os.listdir(dir_name)`
[[Generator#generator expression (generator comprehension)|Generator]] object which lists all contents of a path recursively: `os.walk(path)`
```python
#Travers all the branch of a specified path
for (root,dirs,files) in os.walk('path/to/a/folder',topdown=True):
   print("Directory path: %s"%root)
   print("Directory Names: %s"%dirs)
   print("Files Names: %s"%files)

```
`os.mkdir()` creates a single directory at the specified path. It raises a `FileExistsError` if the directory already exists.
`os.makedirs()` creates all necessary directories in the path if they don't exist. It also raises a `FileExistsError` if any directory in the path already exists.
```python
# Create a directory named "data/reports" in the current working directory
directory_path = "data/reports"
try:
  os.makedirs(directory_path)
  print(f"Directory '{directory_path}' created successfully!")
except FileExistsError:
  print(f"Directory '{directory_path}' or a parent directory already exists.")
```

#### file status
status of a file: `os.stat('fileName.txt')`
change permissions: [StckOvrflw](https://stackoverflow.com/questions/16249440/changing-file-permission-in-python#16249655)
```python
os.chmod(path, stat.S_IRUSR | stat.S_IRGRP | stat.S_IROTH)
```
st_mode attribute of returned `stat_result` object will represent the file type and file mode bits (permissions): `print("\nFile type and file permission mask:", status.st_mode)`
get permissions of a file (*str*):
```python
mode = os.stat('file.txt').st_mode  # Get file mode (permissions)
oct_mode = oct(mode)[-3:]  # Convert file mode to octal notation
print(oct_mode)  # Print file permissions in octal notation
```

#### system
Send ping using the `os.system()` command:
```python
def send_ping(host):
    command = f"ping -c 4 {host}"  # -c specifies the number of packets to send (4 in this case)
    exit_code = os.system(command)
    if exit_code == 0:
        print("Ping successful")
    else:
        print("Ping failed")
```
