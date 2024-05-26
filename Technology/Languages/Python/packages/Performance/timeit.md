#python #time 
Measure execution time of small code snippets
[doc](https://docs.python.org/3/library/timeit.html)

While you can import and call timeit.timeit() from Python as a regular function, it’s usually more convenient to use the command-line interface. You can time the two variants as follows:
```python
$ python -m timeit --setup "nums = [7, 6, 1, 4, 1, 8, 0, 6]" "set(nums)"
2000000 loops, best of 5: 163 nsec per loop

$ python -m timeit --setup "nums = [7, 6, 1, 4, 1, 8, 0, 6]" "{*nums}"
2000000 loops, best of 5: 121 nsec per loop
```

Finally, the [IPython interactive shell](https://ipython.org/) and the [Jupyter Notebook](https://realpython.com/jupyter-notebook-introduction/) have extra support for this functionality with the `%timeit` magic command:
```python
In [1]: numbers = [7, 6, 1, 4, 1, 8, 0, 6]
In [2]: %timeit set(numbers) 
>>> 171 ns ± 0.748 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)
In [3]: %timeit {*numbers} 
>>> 147 ns ± 2.62 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)
```
Again, the measurements indicate that using a set literal is faster. In Jupyter Notebooks, you can also use the `%%timeit` cell-magic to measure the time of running a whole cell.