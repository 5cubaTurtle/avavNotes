#default
Maintain symbolic links determining default commands

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