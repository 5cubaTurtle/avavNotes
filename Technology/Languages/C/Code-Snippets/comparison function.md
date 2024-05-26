The function receives an array, the size of the array, and a value to compare to items in the array.
It returns 1 if the value if found in the array or 0 if not found.
```c
int cmp(int arr[], size_t arrsz, int val)
{
    int sum=0, i;
    for(i=0; i<arrsz; ++i)
        sum += !(arr[i]^val);

     return !!sum;
}
