The pickle module allows you to serialize Python objects to binary format and deserialize them back into Python objects:
```python
import pickle

my_list = [1, 2, 3, 4, 5]

# Open the file in binary write mode
with open('list_data.pickle', 'wb') as file:
    # Serialize the list to binary and write it to the file
    pickle.dump(my_list, file)
```
In this example, we use the `pickle.dump()` function to serialize the my_list to binary format and write it to the file. The file is opened in binary write mode (`'wb'`) using the open() function.

Similarly, to load the list from the binary file, you can use the pickle.load() function:
```python
import pickle
# Open the file in binary read mode
with open('list_data.pickle', 'rb') as file:
    # Load the binary data from the file
    loaded_list = pickle.load(file)

# Print the loaded list
print(loaded_list)
```
This code opens the file in binary read mode (`'rb'`), uses the pickle.load() function to load the binary data from the file into the loaded_list variable, and finally prints the loaded list.

Note that when using pickle, the binary file format is not human-readable like [[Technology/Languages/Python/packages/Data/json]]. It is designed for Python-specific serialization and deserialization.