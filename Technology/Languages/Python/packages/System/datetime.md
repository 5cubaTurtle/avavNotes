convert a string representing a date and time in format *'%Y-%m-%d %H:%M:%S,%f'* to the number of seconds since the epoch (1970-01-01 00:00:00 UTC):
```python
from datetime import datetime

# Define the format of the input time string
time_format = '%Y-%m-%d %H:%M:%S,%f'

# Convert the input time string to a datetime object
input_time = datetime.strptime('2023-02-13 16:01:05,061', time_format)

# Convert the datetime object to the number of seconds since the epoch with milliseconds
return input_time.timestamp()
```

get time:
```python
import datetime
# Get the current time as a datetime object
current_time = datetime.datetime.now()
```
`current_time` will be [[__repr__|represented]] in the format `YYYY-MM-DD HH:MM:SS.ssssss`.
To present only the time w/o the date:
```python
# Format the current time as a string as HH:MM:SS
time_string = current_time.strftime("%H:%M:%S")
short_date_and_time = current_time.strftime("%y%m%d%H%M%S")
```
##### Symbols
Each time symbol is preceded by a `%` sign. A datetime of value (2023, 6, 7, 8, 16, 46, 903397) will produce the following values for each symbol:
- `D` '06/07/23'
- `F` '2023-06-07'
- `T` '08:16:46'
- `Y` 2023 (year)
- `y` 23 (year)
- `m` 06 (month)
- `h` 'Jun' (month)
- `d` 07 (day)
- `a` 'Wed' (day)
- `A` 'Wednesday'
- `H` 08 (hour) (24-hour clock) as a zero-padded decimal number.
- `M` 16 (minutes)
- `S` 46 (seconds)
- `w` 3 (day number of the week), Its modulo of 7. Sunday is 0.
- `W` 23 (week in the year)
- `j` '158' (day of year)
full list [here](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)

convert `"12:30:45"` string to *datetime* format:
```python
time_string = "12:30:45"
# Convert the string to a datetime object
time_obj = datetime.datetime.strptime(time_string, "%H:%M:%S")
```
this will include date of 1900-01-01 because the `strptime()` method expects a complete date-time string. Only use the time component of the `datetime` object by using the `time()` method:
```python
time_only_string = str(time_obj.time())
```

### Set data
Use `replace`:
```python
# Create a datetime object
dt = datetime(2023, 5, 18, 10, 30, 0)
# Set the seconds to a new value
new_dt = dt.replace(second=45)
```
