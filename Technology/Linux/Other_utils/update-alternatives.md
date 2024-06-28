#default
Maintain symbolic links determining default commands
Example from [SO](https://stackoverflow.com/a/75384479/5273667):` update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 60`
The above command says, `/usr/bin/gcc` is the `link` needed and the `name` is `gcc`, the target executable is `/usr/bin/gcc-10` and it has a priority of 60.
### Troublshoot
If
```sh
update-alternatives --config python3
```
outputs the error: "update-alternatives: error: no alternatives for python3"

follow this [SO answer](https://unix.stackexchange.com/a/410851):
```python
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.4 1
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.6 2
```

Then run :
```python
sudo update-alternatives --config python
```

Set python3.6 as default.

Or use the following command to set python3.6 as default:
```python
sudo update-alternatives  --set python /usr/bin/python3.6
```