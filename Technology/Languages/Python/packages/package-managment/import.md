#python 

[guide](https://pymotw.com/3/sys/imports.html#import-path)

The search path for modules is managed as a Python list saved in [[sys#[`sys.path`](https://docs.python.org/3.8/library/sys.html sys.path "Permalink to this definition")|sys.path]]. The default contents of the path include the directory of the script used to start the application and the current working directory.

Optionally, `as Y` can be added after any `import X` statement: `import X as Y`. This renames `X` to `Y` within the script. Note that the name `X` itself is no longer valid. A common example is `import numpy as np`.

#### PYTHONPATH
Augment the default search path for module files
- [doc](https://docs.python.org/3.8/using/cmdline.html#envvar-PYTHONPATH)
[using PYTHONPATH](https://bic-berkeley.github.io/psych-214-fall-2016/using_pythonpath.html) 

The import search-path list can be modified before starting the interpreter by setting the shell variable [[#PYTHONPATH]] to a colon-separated list of directories.
`PYTHONPATH=/my/private/site-packages:/my/shared/site-packages`

show PYTHONPATH:
in shell: `echo $PYTHONPATH`
in python shell:`os.environ['PYTHONPATH']`

#### reloading a package
use [[importlib]]'s reload function to reload a package: `importlib.reload(view)`

### [import statement guide](https://chrisyeh96.github.io/2017/08/08/definitive-guide-python-imports.html):
#### Summary / Key Points
-   `import` statements search through the list of paths in `sys.path`
-   `sys.path` always includes the path of the script invoked on the command line and is agnostic to the working directory on the command line.
-   importing a package is conceptually the same as importing that package’s `__init__.py` file

#### Basic Definitions
-   **module**: any `*.py` file. Its name is the file name.
-   **built-in module**: a “module” (written in C) that is compiled into the Python interpreter, and therefore does not have a `*.py` file.
-   **package**: any folder containing a file named `__init__.py` in it. Its name is the name of the folder.
    -   in Python 3.3 and above, any folder (even without a `__init__.py` file) is considered a package

#### What is an `import`?
When a module is imported, Python runs all of the code in the module file. When a package is imported, Python runs all of the code in the package’s `__init__.py` file, if such a file exists. All of the objects defined in the module or the package’s `__init__.py` file are made available to the importer.

#### Python searches for modules to import:
1.  built-in modules from the Python Standard Library (e.g. `sys`, `math`)
2.  modules or packages in a directory specified by [[sys#[`sys.path`](https://docs.python.org/3.8/library/sys.html sys.path "Permalink to this definition")|sys.path]]:
    1.  If the Python interpreter is run interactively, `sys.path[0]` is the empty string `''`. This tells Python to search the current working directory from which you launched the interpreter, i.e., the output of `pwd` on Unix systems.

        If we run a script with `python <script>.py`, `sys.path[0]` is the path to `<script>.py`.
        
    2.  directories in the [[#PYTHONPATH]] environment variable
    3.  default `sys.path` locations, including remaining Python Standard Library modules which are not built-in

### [adding path to sys.path](https://stackoverflow.com/a/12257807/5273667)
There are a few ways. One of the simplest is to create a `my-paths.pth` file (as described [here](http://docs.python.org/library/site.html)). This is just a file with the extension `.pth` that you put into your system `site-packages` directory. On each line of the file you put one directory name, so you can put a line in there with `/path/to/the/` and it will add that directory to the path.

You could also use the PYTHONPATH environment variable, which contains directories that will be added to `sys.path`. See [the documentation](http://docs.python.org/tutorial/modules.html#the-module-search-path).

#### PYTHONPATH for sudo
`sudo env "PYTHONPATH=$PYTHONPATH" python3 your_script.py`
This command sets the `PYTHONPATH` environment variable explicitly for the `sudo` command. It takes the current value of `PYTHONPATH` from the current shell session and passes it to the `sudo` environment.