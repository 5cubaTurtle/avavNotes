[doc](https://docs.python.org/3/glossary.html#term-file-object)
[file-methods W3](https://www.w3schools.com/python/python_ref_file.asp)


get a [[file-object]]: `fh = open(file, mode)`
close the file after done with it: `fh.close()`

#### read from file
get the text from file: `data = fh.read()`
get a line from a file: `line = fh.readline()`
get all lines:
```python
# Open the file in read mode
with open('file.txt', 'r') as f:
    # Read the lines of the file into a list
    lines = f.readlines()
```
The resulting `lines` list will contain all the lines of the file as strings, where each string represents a single line. Each element in the list will include the newline character `\n` at the end of the line, so you may want to remove it if you don't need it using the `strip()` method. The `strip()` method removes leading and trailing whitespaces from a string, including the newline character:
```python
# Open the file in read mode
with open('file.txt', 'r') as f:
    # Read the lines of the file into a list, removing the newline character
    lines = [line.strip() for line in f]
```

#### write to file
```python
file = open("example.txt", "w") # open in 'write' mode
file.write("Hello, world!\n")
file.write("This is a sample file.")
file.close()
```
See [[open()]] for other modes (`w`, `r`, `a`, `w+`, `r+` or `a+`).

### flush
This method forces the contents of a file in memory to be written to the physical storage device.
Here's a breakdown of what `fileObject.flush()` typically does:

1. **Buffering:** When you write data to a file, it's often not written directly to the disk immediately. Instead, the data is stored in a temporary buffer in memory for efficiency.
2. **Flushing:** The `flush()` method forces the data from the buffer to be written to the disk. This ensures the data is physically written even if the program crashes or encounters an error before the file is closed.

#### When is `flush()` useful?
There are a few scenarios where `flush()` can be helpful:

- **Critical data:** If you're working with critical data that needs to be saved immediately, `flush()` can ensure it's written to disk even if the program terminates unexpectedly.
- **Data integrity:** In some cases, you might want to guarantee data is written before continuing the program to avoid inconsistencies. `flush()` can help achieve this.