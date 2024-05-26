#search 
[regexr](https://regexr.com/)
in python, [[re]] is the RegEx library

### Language includes
c++: `#include <regex>`
[[re|python]]: `import re`
### Anchors
- `^` start of the line/string.
- `$` end of the line/string.
- `.` any single character
- `*` any characters

### useful patterns
Email validation:
```regex
^\\w+([-+.']\\w+)*@\\w+([-.]\\w+)*\\.\\w+([-.]\\w+)*$
```
