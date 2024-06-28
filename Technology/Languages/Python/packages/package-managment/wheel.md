A *wheel* is a python packaged (binary) code, ready for publication. It contains the metadata a python package manager needs to install the package.

When installing from source, some packages, such as Kivy, require additional steps, like compilation.

Contrary, wheels (files with a `.whl` extension) are pre-built distributions of a package that has already been compiled. These wheels do not require additional steps when installing them.

When a wheel is available on [pypi.org](https://pypi.python.org/pypi) (“Python Package Index”) it can be installed with [[pip]]. For example when you execute `python -m pip install kivy` in a command line, this will automatically find the appropriate wheel on PyPI.

When downloading and installing a wheel from a local file, use the command `python -m pip install <wheel_file_name>`, for example:
```sh
python -m pip install C:\Kivy-1.9.1.dev-cp27-none-win_amd64.whl
```


To create the binary distribution: `python setup.py bdist_wheel`
- `bdist_wheel` stands for binary distribution wheel, it will generate the `.whl` file. This is the package.
### What are nightly wheels[¶](https://kivy.org/doc/stable/gettingstarted/installation.html#what-are-nightly-wheels "Permalink to this heading")
Every day we create a snapshot wheel of the current development version of Kivy (‘nightly wheel’). You can find the development version in the master branch of the [Kivy Github repository](https://github.com/kivy/kivy).

As opposed to the last _stable_ release (which we discussed in the previous section), nightly wheels contain all the latest changes to Kivy, including experimental fixes. For installation instructions, see [Pre-release, pre-compiled wheels](https://kivy.org/doc/stable/gettingstarted/installation.html#kivy-nightly-install).

>[!Warning]
Using the latest development version can be risky and you might encounter issues during development. If you encounter any bugs, please report them.


