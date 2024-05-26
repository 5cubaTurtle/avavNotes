#pandas
[w3s](https://www.w3schools.com/python/pandas/pandas_series.asp)
A *Series* is like a column in a table. It is a one-dimensional array holding data of any type.
```python
a = [1, 7, 2]  
myvar = pd.Series(a)
myvar[1]  # is 7
```
If nothing else is specified, the values are labeled with their index number, i.e 0, 1, 2, ... etc.

With the `index` argument, you can name your own labels:
```python
a = [1, 7, 2]  
myvar = pd.Series(a, index = ["x", "y", "z"])
a["y"]   # is 7
```

You can also use a key/value object, like a dictionary, when creating a Series.
Create a simple Pandas Series from a dictionary:
```python
calories = {"day1": 420, "day2": 380, "day3": 390}  
myvar = pd.Series(calories)
```
The keys of the dictionary become the labels.
To select only some of the items in the dictionary, use the `index` argument and specify only the items you want to include in the Series.

Create a Series using only data from `"day1"` and `"day2"`:
```python
calories = {"day1": 420, "day2": 380, "day3": 390}  
myvar = pd.Series(calories, index = ["day1", "day2"])
myvar[2]
```
`myvar[2]` will fail with out of bounds [[Exception#Exception types|IndexError]].

## Filtering
get all the rows greater than 886:
```python
type(bl) # pandas.core.series.Series
bl.loc[bl > 886]
```
