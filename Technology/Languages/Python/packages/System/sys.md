#python 
provides  access to variables used or maintained by the interpreter and to functions that interact strongly with the interpreter. It is always available.

flush the [[stdout]] stream: `sys.stdout.flush()`

##### [`sys.argv`](https://docs.python.org/3.8/library/sys.html#sys.argv "Permalink to this definition")
The list of command line arguments passed to a Python script. `argv[0]` is the script name (it is operating system dependent whether this is a full pathname or not). If the command was executed using the [`-c`](https://docs.python.org/3.8/using/cmdline.html#cmdoption-c) command line option to the interpreter, `argv[0]` is set to the string `'-c'`. If no script name was passed to the Python interpreter, `argv[0]` is the empty string.

To loop over the standard input, or the list of files given on the command line, see the [`fileinput`](https://docs.python.org/3.8/library/fileinput.html#module-fileinput "fileinput: Loop over standard input or a list of files.") module.

>On Unix, command line arguments are passed by bytes from OS. Python decodes them with filesystem encoding and “surrogateescape” error handler. When you need original bytes, you can get it by `[os.fsencode(arg) for arg in sys.argv]`.

##### [`sys.path`](https://docs.python.org/3.8/library/sys.html#sys.path "Permalink to this definition")
A list of strings that specifies the search path for modules. Initialized from the environment variable [[import|PYTHONPATH]], plus an installation-dependent default.

As initialized upon program startup, the first item of this list, `path[0]`, is the directory containing the script that was used to invoke the Python interpreter. If the script directory is not available (e.g. if the interpreter is invoked interactively or if the script is read from standard input), `path[0]` is the empty string, which directs Python to search modules in the current directory first. Notice that the script directory is inserted _before_ the entries inserted as a result of [`PYTHONPATH`](https://docs.python.org/3.8/using/cmdline.html#envvar-PYTHONPATH).

A program is free to modify this list for its own purposes. Only strings and bytes should be added to [`sys.path`](https://docs.python.org/3.8/library/sys.html#sys.path "sys.path"); all other data types are ignored during import.

print `sys.path` from shell:   `python -c "import sys; print(sys.path)"`

>See also: Module [`site`](https://docs.python.org/3.8/library/site.html#module-site "site: Module responsible for site-specific configuration.") This describes how to use .pth files to extend [`sys.path`](https://docs.python.org/3.8/library/sys.html#sys.path "sys.path").

Note that `sys.path` contains _directories_ not files. You can't "add a file to `sys.path`". You always add its directory and then you can import the file.
To add the directory `/home/me/mypy` to the path, just do:
```python
import sys
sys.path.append("/home/me/mypy")
```

> Common issue: If a module appears in several locations in `sys.path`, only the 1st occurrence will be considered. If you attempt to import from a module (like this `from brcv_on_robot.line_detection.line_detect import LineDetect`) which is defined not in the 1st occurrence, a [[ModuleNotFoundError]] exception will be thrown but it will not state from which location python failed to import the requested module. In this case try importing from the location directly (like this: `from brcv_on_robot import LineDetect`, it will then state which is the 1st occurrence of `brcv_on_robot`).

##### [`sys.modules`](https://docs.python.org/3.8/library/sys.html#sys.modules)
A [[dict]] containing mapping the names of imported modules. The contents of `sys.modules` change as new modules are imported.

`sys.builtin_module_names` - all builtin modules

##### python version and platform
`sys.version` and `sys.platform`
