#json

##### [json.load()](https://docs.python.org/3/library/json.html#json.load "Permalink to this definition")
deserialize a file into a json object
It reads a [[Technology/Languages/Python/packages/Data/json]] encoded file containing JSON data and returns a Python object that represents the JSON data.

##### [json.loads()¶](https://docs.python.org/3/library/json.html#json.loads "Permalink to this definition")
deserialize a string into a json object

The Python object returned by `json.loads()` can be a dictionary, a list, a string, a number, a boolean, or `None`, depending on the JSON data. For example, if the JSON data represents an object with keys and values, `json.loads()` will return a [[dict|dictionary]] that maps the keys to their corresponding values. If the JSON data represents an array, `json.loads()` will return a [[list]] of the elements in the array.

Here is an example of using `json.loads()` to load a JSON string:
```python
import json

# JSON string
json_string = '{"name": "John Smith", "age": 42, "is_student": false}'

# Deserialize the JSON string
data = json.loads(json_string)
```
the `data` will look like this:
```python
{'name': 'John Smith', 'age': 42, 'is_student': False}
```
Note that the boolean value `false` in the JSON data is deserialized as the Python boolean `False`. The keys and strings are also converted from JSON format to Python format, so the key `is_student` is converted to a string without spaces.

If the input JSON string is well-formed, it will always return a Python object. However, if the input JSON string is malformed, `json.loads()` can raise a `JSONDecodeError` exception.

#### null
In terms of the content of the JSON string, it is possible for the deserialized Python object to be `None`. This will occur if the JSON data contains a `null` value. For example, the following JSON string contains a `null` value:
```json
{
    "name": "John",
    "age": null,
    "city": "New York"
}
```
in python
```python
{'name': 'John', 'age': None, 'city': 'New York'}
```
`age` key in the deserialized Python object is `None`.

JSON string with only the `null` value:
```python
json_string = 'null'
data = json.loads(json_string)
print(data)
>>> None
```
In this case, the deserialized Python object is `None` because the JSON string contains only the `null` value.

##### Read from file
```python
with open(calibration_path) as f:  
    crop_data = json.load(f)
```

##### copy
deep copy:
`copyOfData = data.copy()`

### remote
```python
# Read the contents of the remote JSON file
stdin, stdout, stderr = ssh_client.exec_command(f"cat {remote_file_path}")
json_string = stdout.read().decode()

# Parse the JSON data
data = json.loads(json_string)

# Modify the JSON data
data["foo"] = "bar"

# Convert the JSON data back to a string
new_json_string = json.dumps(data)

# Write the modified JSON data back to the remote file
stdin, stdout, stderr = ssh_client.exec_command(f"echo '{new_json_string}' > {remote_file_path}")
```
The `ssh_client.exec_command()` and `json_string = stdout.read().decode()` are functions of [[paramiko]] package