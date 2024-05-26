#python 
[referance](https://pip.pypa.io/en/stable/cli/pip/)
### [PIP](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/)
help:   `pip -h`

> [!NOTE] "Package"
In  the following examples `<package>`  refers to *distribution package* . See [import package vs distribution package](https://packaging.python.org/en/latest/discussions/distribution-package-vs-import-package/#distribution-package-vs-import-package) for explanation.

install a package:   `pip install <package>`
install a package to some specific python version:   `python3 -m pip install <package>`
install specific version:   `pip install -Iv` (i.e. `pip install -Iv MySQL_python==1.2.2`)
-   `-I` stands for `--ignore-installed` which will ignore the installed packages, overwriting them.
-   `-v` is for verbose. You can combine for even more verbosity (i.e. `-vv`) up to 3 times (e.g. `-Ivvv`).

upgrade a package: `pip install -U <package>`
show installed packages:   `pip list`
show info about specific package `pip show <package>`
upgrade pip: `python -m pip install --upgrade pip`
#### requirements.txt
Install from *requirements.txt*:  `pip instal -r requirement.txt`
List installed packages in requirements format: `pip freeze`
Generate a *requirements.txt*:`pip freeze > requirements.txt`

#### packages location in file
For a [[Virtual-environment|virtual environment]], the packages are stored in the `site-packages` directory within the virtual environment directory:`/path/to/venv/lib/pythonX.Y/site-packages/`.

For a system-wide Python installation, the packages are stored in the global `site-packages` directory. This location can vary depending on the Python installation method and the operating system. In general, it can be found in a path like `/usr/lib/pythonX.Y/site-packages/` or `/usr/local/lib/pythonX.Y/dist-packages/`.

You can locate the exact path of the `site-packages` directory by running the following command in your Python environment:
```bash
python -c "import site; print(site.getsitepackages())"
```
This command will output the path to the `site-packages` directory where the pip-installed packages are stored in your Python environment.

Use `pip show` to see the location of a specif package.

#### package resolution
When you activate a virtual environment (venv), it is designed to isolate the Python environment from the system-wide Python installation. However, the behavior of `pip list` inside a virtual environment can sometimes show globally installed packages due to how Python resolves package paths.

Here are a few reasons why you might see globally installed packages when running `pip list` inside a virtual environment:

1. [[import#PYTHONPATH|PATH Environment Variable]]:
   - When you activate a virtual environment, the virtual environment's `bin` directory is added to the beginning of the `PATH` environment variable.
   - However, the system-wide `bin` directory where global packages are installed remains in the `PATH`.
   - This can lead to the global `pip` being used inadvertently when running `pip list`.

2. **Python Path**:
   - Python looks for packages in multiple locations, including the virtual environment's `site-packages` directory and the global `site-packages` directory.
   - If a package is installed globally and the virtual environment does not have its own version of that package, Python will use the global package.

3. **User Site Packages**:
   - Python also checks the user site-packages directory for packages.
   - If a package is installed using the `--user` flag globally, it may be visible in the virtual environment.

To ensure that you only see packages installed within the virtual environment when running `pip list`, you can take the following steps:
- Use `python -m pip list` instead of `pip list` to ensure that the correct `pip` associated with the virtual environment is used.
- Check the `sys.path` within the Python interpreter to see which directories are being used to import packages.
- Verify that the virtual environment is activated correctly before running `pip list`.
### Troubleshooting
#### SSLError when upgrading PIP
I get the following error while trying to upgrade pip:  
the command I ran:  
`/home/ava/PycharmProjects/tools/venv/bin/python -m pip install --upgrade pip`
the output:  
```shell
Requirement already satisfied: pip in ./venv/lib/python3.8/site-packages (21.3.1)  
Collecting pip  
  WARNING: Retrying (Retry(total=4, connect=None, read=None, redirect=None, status=None)) after connection broken by 'SSLError(SSLCertVerificationError(1, '[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: self signed certificate in certificate chain (_ssl.c:1131)'))': /packages/09/bd/2410905c76ee14c62baf69e3f4aa780226c1bbfc9485731ad018e35b0cb5/pip-22.3.1-py3-none-any.whl

ERROR: Could not install packages due to an OSError: HTTPSConnectionPool(host='[files.pythonhosted.org](http://files.pythonhosted.org)', port=443): Max retries exceeded with url: /packages/09/bd/2410905c76ee14c62baf69e3f4aa780226c1bbfc9485731ad018e35b0cb5/pip-22.3.1-py3-none-any.whl (Caused by SSLError(SSLCertVerificationError(1, '[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: self signed certificate in certificate chain (_ssl.c:1131)')))  
  
WARNING: You are using pip version 21.3.1; however, version 22.3.1 is available.  
You should consider upgrading via the '/home/ava/PycharmProjects/tools/venv/bin/python -m pip install --upgrade pip' command.
```

was solved by [this](https://stackoverflow.com/questions/49324802/pip-always-fails-ssl-verification) answer on StkOvrflw with this command:
`python -m pip install --user --trusted-host files.pythonhosted.org --trusted-host pypi.org --trusted-host pypi.python.org --upgrade pip`
- the `--user` flag was omitted since I  was in a [[Virtual-environment|venv]]

> [!NOTE] 
> The same solution can be used for installing any other package for a [[Virtual-environment|venv]]:
> `/home/ava/PycharmProjects/tools/venv/bin/python -m pip install pandas`


#### \_libastro.c:3:10: fatal error: Python.h: No such file or directory
Try installing *python-dev*: `sudo apt install python3-dev`
If its for python2 then: `sudo apt install python2-dev`

#### external packages interfere with venv
unset the [[import#PYTHONPATH|PYTHONPATH]] in venv's *activate* file:
```sh
# Save old PYTHONPATH
_OLD_PYTHONPATH="$PYTHONPATH"
unset PYTHONPATH

# insied the deactivate function:
eactivate () {
	...
	...
	...
	# reset old PYTHONPATH
    # ! [ -z ${VAR+_} ] returns true if VAR is declared at all
    if ! [ -z "${_OLD_PYTHONPATH:+_}" ] ; then
        PYTHONPATH="$_OLD_PYTHONPATH"
        export PYTHONPATH
        unset _OLD_PYTHONPATH
    fi
}
```

#### [ModuleNotFoundError: No module named 'distutils.util'](https://askubuntu.com/questions/1239829/modulenotfounderror-no-module-named-distutils-util)
Solution
```python
sudo apt install python3.x-distutils
```

#### [pip3 install not working - No module named 'pip.\_vendor.pkg_resources'](https://stackoverflow.com/questions/49478573/pip3-install-not-working-no-module-named-pip-vendor-pkg-resources)
Or in my case it was:
```
ModuleNotFoundError: No module named 'pip._vendor.six.moves'
```
Solution:
```sh
curl -sS https://bootstrap.pypa.io/get-pip.py | python3
```
