#python 
data structures for data analysis, time series, and statistics
[doc](https://pandas.pydata.org/docs/), [w3schools](https://www.w3schools.com/python/pandas/default.asp)

`import pandas as pd`
check version: `pd.__version__`

[[dict]] and [[list]] example:
```python
mydataset = {  
  'cars': ["BMW", "Volvo", "Ford"],  
  'passings': [3, 7, 2]  
}  
myvar = pd.DataFrame(mydataset)
```

### methods
Pandas uses the `mean()` `median()` and `mode()` methods to calculate the respective values for a specified column. [[Mean]], [[Median]], [[Mode]].

convert date format:
```python
df['Date'] = pd.to_datetime(df['Date'])
```

### options
- *pd.options.display.max_rows* - If the DataFrame contains more than *max_rows* rows, the `print(df)` statement will return only the headers and the first and last 5 rows.
### data-structures
[[Series]]
[[DataFrame]]
[[Cleaning-Data]]
