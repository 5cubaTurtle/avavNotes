#python 
The CPython interpreter scans the command line and the environment for various settings.
- [doc](https://docs.python.org/3.8/using/cmdline.html#)

running python code from command-line:  `python -c "<python_code>"`
	for example `python -c "import sys; print(sys.path)"`
	this could be used to run specific function from some pyton file:
	`python -c "import somePackage; print(somePackage.someElement)"`
