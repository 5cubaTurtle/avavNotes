#python #virtual-environment
[doc](https://docs.python.org/3/library/venv.html#module-venv)

- Install venv:   `sudo apt install python3.8-venv`
- Creating an env:   `python -m venv <env_name>`, this will create a dir named *env_name*
	- This will use the system default python version. Use the appropriate python link to set the desired version. For example: `python3.12 -m ...` for *python3.12*
- To delete the env, [[Technology/Linux/File-System/utilities/rm|remove]] the venv follder: `rm -r <env_name>`
- Activating the env:  `source path/to/env/bin/activate`
- To install a package to a venv use [[PIP|pip]] install with the venv active
- Deactivate the env, use:`deactivate`
- Print location of python interpreter: `python -c "import sys; print(sys.executable)"`,
	- To see where packages are installed see [[PIP#packages location in file]].
>[!Note]
>When you activate a virtual environment, your `PATH` variable is changed. On Linux and MacOS, you can see it for yourself by printing the path with `echo $PATH`

The *.venv/bin/activate* file sets/unsets the [[environment-variables]]. This is done when activating the venv: `source path/to/env/bin/activate`
### Is this true?
install package to an venv:
```sh
workon py3cv3  # use your virtual environment name
pip install imagezmq
```
