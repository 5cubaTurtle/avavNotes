---
Invocation: import re
---
A [[Technology/Protocol/RegEx]] library

```python
import re
```

extract the time in format "*2023-02-13 16:01:05,035*" from the line:
```python
# Define a regular expression to match the substring
regex = re.compile(r'\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2},\d{3}')

# Search for the substring in the given line
line = '[rospy.client][INFO] 2023-02-13 16:01:05,035: init_node, name[/cleaning_algorithm], pid[37930]'
match = regex.search(line)

# Check if a match was found and print the result
if match:
    print('Match found:', match.group())
else:
    print('No match found.')
```

extract the word between `/learning/` and `/`,
then replace every `-` in it to `_`:
```python
def acquire_course_name(self):
	self._course_name = re.sub("-", "_", re.search("/learning/(.+?)/", self.brwsr.current_url)[1])
```