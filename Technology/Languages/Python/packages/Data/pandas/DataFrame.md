#pandas 
[w3s](https://www.w3schools.com/python/pandas/pandas_dataframes.asp)
Data sets in Pandas are usually multi-dimensional tables, called DataFrames.

### creation
Create a DataFrame from two Series:
```python
data = {  
  "calories": [420, 380, 390],  
  "duration": [50, 40, 45]  
}  
myvar = pd.DataFrame(data)

myvar  #  DataFrame is like a table with rows and columns.
>>>   calories  duration
  0       420        50
  1       380        40
  2       390        45
```

Define the columns:
```python
s = pd.DataFrame([(0.0, np.nan,-2.0,2.0),
                    (np.nan, 2.0, np.nan, 1),
                    (2.0, 5.0, np.nan,9.0),
                    (np.nan, 4.0,-3.0, 16.0)],
                   columns=list('abcd'))
```
#### from file
Load df from csv: `df = pd.read_csv('data.csv')`
Load df from json: `df = pd.read_csv('data.csv')`

## data manipulation
see [[Cleaning-Data]]
### loc\[ \]
>see `help(df.loc)` for more usage examples

`loc[]` returns a Pandas Series:
```python
myvar.loc[0]
>>> calories    420
    duration     50
    Name: 0, dtype: int64

# Return row namved 0 and 1:
df.loc[[0, 1]]  # use a list of indexes
```
If indexes are given names, these names could be used to retrieve specific row(s):
`df.loc['day2', 'day7']`.

Replace a specific value:
Set "Duration" = 45 in row 7: `df.loc[7, 'Duration'] = 45`

Delete rows where "Duration" is higher than 120:
```python
for x in df.index:  
  if df.loc[x, "Duration"] > 120:  
    df.drop(x, inplace = True)
```

### [Split a column of lists](https://stackoverflow.com/questions/35491274/split-a-pandas-column-of-lists-into-multiple-columns)
Split the column of lists named *teams* into separate columns for each index in the list:
```python
df3 = df2.teams.apply(pd.Series)
df3.columns = ['team1', 'team2']
```
## data presentation
Convert df to string: `df.to_string()`
Headers and the first 10 rows of a DataFrame:`df.head(10)`
Headers and the last 5 rows of a DataFrame:`df.tail()`
Info of DataFrame:`df.info()`
> If you have a large DataFrame with many rows, the dunders [[__repr__]] and [[__str__]] (i.e. when printing the df) will only return the first 5 rows, and the last 5 rows. See *display.max_rows* in [[pandas-main-note#options]]

rename axis: `df.set_axis(['ekf_angle'], inplace=True, axis='columns')`
### plotting
```python
import matplotlib.pyplot as plt
df.plot()
plt.show()
```

- **scatter** plot. A scatter plot needs an x- and a y-axis:
`df.plot(kind = 'scatter', x = 'Duration', y = 'Calories')`.
- **histogram** plot. A histogram needs only one column. A histogram shows us the frequency of each value in a column: `df["Duration"].plot(kind = 'hist')`

[plot scatter](https://stackoverflow.com/a/51654092):
```python
plt.plot(df.x, df.y, marker='.', linestyle='none')
```
## data analysis
calculate [[Correlation]]s between columns: `df.corr()`. Read [w3s](https://www.w3schools.com/python/pandas/pandas_correlations.asp) for more details.