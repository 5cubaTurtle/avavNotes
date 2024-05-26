---
Invocation: import argparse
---
Parser for command-line options, arguments and sub-commands
[doc](https://docs.python.org/3/library/argparse.html#module-argparse "Permalink to this headline")

#### argument type and values
By default arguments treated as strings. Treat argument as an *int*:
```python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument("square", help="display a square of a given number",
                    type=int, choices=[0, 1, 2])
args = parser.parse_args()
print(args.square**2)
```
- `typw=int` states the allowed type of the argument to the parameter
- `choices=[9, 1, 2]` state the actual allowed values.
- `action="count"` this could be used instead of `choices` to set an *int* value to the parameter by passing the parameter several times. [example](https://docs.python.org/3/howto/argparse.html#combining-positional-and-optional-arguments)
- `default=0` could be set to set the default value to other than `None`.

#### optional argument
add the suffix `--`  to the name of the argument to declare it as optional:
```python
parser.add_argument("--verbosity", help="increase output verbosity")
```
The optional argument requires some value followed by it. To avoid providing a value use [`nargs='?'`](https://docs.python.org/3/library/argparse.html#nargs), as in [this SO answer](https://stackoverflow.com/a/15301183). For it to behave as a flag, use the [`action="store_true"`](https://docs.python.org/3/library/argparse.html#action) parameter in `add_argument()`.

#### short option
```python
parser.add_argument("-v", "--verbose", help="increase output verbosity",
                    action="store_true")
```

### [Conflicting options](https://docs.python.org/3/howto/argparse.html#conflicting-options "Permalink to this headline")
Use exclusion groups to prevent usage of conflicting options:
```python
group = parser.add_mutually_exclusive_group(required=True)
group.add_argument("-v", "--verbose", action="store_true")
group.add_argument("-q", "--quiet", action="store_true")
```
Now the `-v` and `-q` flags will be prevented from being used simultaneously. The `required` flag in the constructor of the group will force to provide at least one of the group's members.

### program description
Program description could be inputted at the creation of the parser:
```python
parser = argparse.ArgumentParser(description="calculate X to the power of Y")
```

### [subparsers](https://docs.python.org/3/library/argparse.html#sub-commands)
[StkOvrflw example](https://stackoverflow.com/a/17074215):
Depending on initial arguments, parse following arguments using *subparsers*:
```python
parser = argparse.ArgumentParser()
subparsers = parser.add_subparsers(help='types of A')
parser.add_argument("-v")

a_parser = subparsers.add_parser("A")
b_parser = subparsers.add_parser("B")

a_parser.add_argument("something", choices=['a1', 'a2'])
a_parser.set_defaults(func=func_a)  # start 'func_a' if 'a' sub_parser was selected

parser.set_defaults(func=default_func)  # start some default function if no sub_parser was selected
```
First provide either `A` or `B` . If `A` was provided, then `a1` or `a2` is needed. `-v` is optional.

### The Namespace object [doc](https://docs.python.org/3/library/argparse.html#the-namespace-object "Permalink to this headline")
Simple class used by default by [`parse_args()`](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.parse_args "argparse.ArgumentParser.parse_args") to create an object holding attributes and return it.
If you prefer to have dict-like view of the attributes, you can use the standard Python idiom, [`vars()`](https://docs.python.org/3/library/functions.html#vars "vars"): `args = vars(parser.parse_args())`







