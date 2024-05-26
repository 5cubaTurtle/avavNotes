#python #float

[Python issues and limitations](https://docs.python.org/3/tutorial/floatingpoint.html)
[General issues](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html)
[Print format float values](https://appdividend.com/2022/06/23/how-to-format-float-values-in-python/)
### f-string formatting
```python
x = 211911461911461819112146
y = 2**70
z = x / y

print(f'{z:.2f}')
>>> 179.50

# another example
f"{ekf:>6.1f}"  # print 'ekf' with 6 space padding from left, one decimal place
```
It works well with long calculations with operators and does not need parenthesis.

##### print format
| Number| Format | Output | Description |
|---------|---------|---------|---------|
|3.1415926|{:.2f}|3.14|Format float 2 decimal places|
|3.1415926|{:+.2f}|+3.14|Format float 2 decimal places with sign
|-1|{:+.2f}|-1.00|Format float 2 decimal places with sign
|2.71828|{:.0f}|3|Format float with no decimal places
|4|{:0>2d}|04|Pad number with zeros (left padding, width 2)
|4|{:x<4d}|4xxx|Pad number with x’s (right padding, width 4)|
|10|{:x<4d}|10xx|Pad number with x’s (right padding, width 4)
|1000000|{:,}|1,000,000|Number format with comma separator
|0.35|{:.2%}|35.00%|Format percentage
|1000000000|{:.2e}|1.00e+09|Exponent notation
|11|{:11d}|        11|Right-aligned (default, width 10)
|11|{:<11d}|11|Left-aligned (width 10)
|11|{:^11d}|    11|Center aligned (width 10)

> Warning: [[math#Modulo math.fmod()|modulo]] operator on floats could have undesirable results.

#### set precision by round()
```python
0.06/340  # 0.0001764705882352941
# round to 7 places after decimal point:
round(0.06/340, 7)  # 0.0001765
```

##### represent as a ratio:
Python provides tools that may help on those rare occasions when you really _do_ want to know the exact value of a float. The [`float.as_integer_ratio()`](https://docs.python.org/3/library/stdtypes.html#float.as_integer_ratio "float.as_integer_ratio") method expresses the value of a float as a fraction:
```python
>>> x = 3.14159
>>> x.as_integer_ratio()
(3537115888337719, 1125899906842624)
```
Since the ratio is exact, it can be used to losslessly recreate the original value:
```python
>>> x == 3537115888337719 / 1125899906842624
True
```
