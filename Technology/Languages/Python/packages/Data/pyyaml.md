
example.yaml
```yaml
name: John
age: 30
city: New York
```
parse the yaml file:
```python
import yaml
with open('example.yaml', 'r') as f:
    data = yaml.safe_load(f)
print(data)
>>> {'name':'John', }
```

