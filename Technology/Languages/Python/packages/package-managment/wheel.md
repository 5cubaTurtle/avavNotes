A *wheel* is a python packaged (binary) code, ready for publication. It contains the metadata a python package manager needs to install the package.

installation: `pip install wheel`

to create the binary distribution: `python setup.py bdist_wheel`
- `bdist_wheel` stands for binary distribution wheel, it will generate the `.whl` file. This is the package.

