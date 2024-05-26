#pandas 
links: [w3s](https://www.w3schools.com/python/pandas/pandas_cleaning.asp), [askpython](https://www.askpython.com/python/examples/nan-in-numpy-and-pandas)

### find bad data
[[NaN]]: `df.isnull()`
duplicates: `df.duplicated()`
remove duplicates: `df.drop_duplicates()`
to fix the date use the `to_datetime()` from the [[pandas-main-note#methods]]
### fillna
replace NaNs with 0: `df.fillna(0)`
replace specific values column-wise:
```python
s = pd.DataFrame([(0.0, np.nan,-2.0,2.0),
                    (np.nan, 2.0, np.nan, 1),
                    (2.0, 5.0, np.nan,9.0),
                    (np.nan, 4.0,-3.0, 16.0)],
                   columns=list('abcd'))
values = {'a':0, 'b':1, 'c':2, 'd':3}
s.fillna(value=values)
```
That means all the NaNs under one column will be replaced with the same value.
You can also use [[Interpolation]] to fill the missing values in a data frame.
> use `inplace=True` to edit the original df instead of returning a new df.
### dropna
Drop rows with NaNs: `df.dropna()`
Drop columns with NaNs: `df.dropna(axis='columns')`
By default `dropna()` returns new df. To change the original df use: `df.dropna(inplace=True)`.
Remove rows with a NULL value in the *"Date"* column:
```python
df.dropna(subset=['Date'], inplace = True)
```

