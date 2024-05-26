#python 
### Escape characters
- `\n`  new line

### Color
print text in color by using [[color#codes|ANSI escape codes]]:
```python
print("\033[1;31;40mRed text\033[0m")
```
`\033[1;31;40m` sets the text color to red, and `\033[0m` resets the text color to the default (i.e., no color). You can modify the escape code to change the color to other colors. Here are the meanings of the individual codes:

-   `\033`: This is the escape character.
-   `[1;31;40m`: This sets the color to red. The `1` makes the text bold, the `31` sets the text color to red, and the `40` sets the background color to black.
-   `\033[0m`: This resets the text color to the default.

##### print_in_color
```python
def print_color(text, color):
    colors = {
        'black': '0;30',
        'red': '0;31',
        'green': '0;32',
        'yellow': '0;33',
        'blue': '0;34',
        'purple': '0;35',
        'cyan': '0;36',
        'white': '0;37'
    }
    if color not in colors:
        raise ValueError(f'Invalid color {color}.')
    color_code = colors[color]
    print(f'\033[{color_code}m{text}\033[0m')

# usage
print_color('Hello, world!', 'green')
```
