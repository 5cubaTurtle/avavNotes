#python, #iterator, #generator 

##### [how to create Iterators](https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python/)

```python
i = iter([1,2,3,4,5])
next(i)  # outputs: 1
next(i)  # outputs: 2
next(i)  # outputs: 3
```

If you wanted to print out just the first line of a 10 gigabyte log file, you could do this:
```python
print(next(open('giant_log_file.txt')))
```
output: "This is the first line in a giant file"
