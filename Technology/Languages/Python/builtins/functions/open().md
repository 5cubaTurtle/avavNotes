#python #file-system

get a [[file-object]]: `fh = open(file, mode)`
- the `mode` is a string of 1-3 characters:

| `mode` | Description                                                                      |
| ------ | -------------------------------------------------------------------------------- |
| `'w'`  | Write mode                                                                       |
| `'r'`  | Read mode                                                                        |
| `'a'`  | Append mode                                                                      |
| `'w+'` | Create the file if it does not exist and then open it in write mode              |
| `'r+'` | Open the file in the read and write mode                                         |
| `'a+'` | Create the file if it does not exist and then open it in append mode             |
| `wb`   | write binary mode (could be appeneded the + or the `w` exchanged for `r` or `a`) |

close the file after done with it: `fh.close()`

with [[contex-manager]]:
```python
with open("timer.py") as fp:
	print("".join(ln for ln in fp if ":" in ln))
```
