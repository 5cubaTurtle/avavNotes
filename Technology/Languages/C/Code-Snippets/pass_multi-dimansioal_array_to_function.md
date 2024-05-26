- `foo(int arr[][num])`:
```c
void foo1(int arr[2][3])
{
    int i, j;
    for(i=0; i<2; ++i)
    {
        for(j=0; j<3; ++j)
            printf("&arr[%d][%d]= %p\t", i, j, (void*)&arr[i][j]);
        printf("\n");
    }
}
```

- `foo(int *arr, height, width)`:
```c
void foo2(int *arr,int height,int width)
{
    int i, j;
    for(i=0; i<height; ++i)
    {
        for(j=0; j<width; ++j)
        {
            printf("*arr at %d,%d= %d\t", i, j, *( arr + i*height + j ));
            printf("arr at %d,%d= %p\t", i, j, (arr + i*height + j));
        }
        printf("\n");
    }
}
```

```c
typedef int arr_t[num]
     foo (arr_t *arr, height)

int (* arr)[num]
```

arrays which are not sequential in memory:
```c
	int **arr, height, width
	int arr[]
```

main:
```c
int main (int argc, char **argv, char **envp)
{
    int arr[] = {1, 3, 23, 4, 0, 99, 10};
    int x = cmp(arr, 7, 0);
    int arr1[2][3] ={{3, 4, 12},
					 {9, 0, 10}};

    printf("x=%d\n",x);
    printf("count 86:%d\n", count(86));
    printf("\n");
    foo1(arr1);
    printf("\n");
    foo2(&arr1, 2, 3);
    return 0;
}
```