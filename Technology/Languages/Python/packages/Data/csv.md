Create a csv file
```python
import csv

data = eval('"[[0, 119, 618, 527, 1112], [1, 633, 1117, 551, 1132], [2, 1145, 1627, 573, 1151], ... [21, 3228, 3607, 2010, 2828], [22, 3549, 3929, 2031, 2842]]"')

with open('data.csv', 'w', newline='') as csvfile:
  writer = csv.writer(csvfile)
  for row in data:
    writer.writerow(row)

print("CSV file created successfully!")
```