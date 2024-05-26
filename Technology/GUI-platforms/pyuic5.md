#python 
Compile Qt5 user interfaces to Python code.
It takes *.ui* input file which is produced by [[QtDesigner]].

compile executable:`pyuic5 -xo login_box.py login_box.ui`
- `-o, --output=FILE` provide output file to this option, otherwise output will be written to *stdout*.
- `-x, --execute` produce executable 