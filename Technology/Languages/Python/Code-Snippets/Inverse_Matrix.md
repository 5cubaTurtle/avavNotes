
```python
def inverse(sqr):
     x,y,inv,A=0,0,[],[]
     while y < len(sqr):
          while x < len(sqr):
               A.append(sqr[x][y])
               x=x+1
          x=0
          inv.append(A)
          A=[]
          y=y+1
     return inv
```