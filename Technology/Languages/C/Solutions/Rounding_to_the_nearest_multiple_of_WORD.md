round down:
```c
val = ( val & ~(WORD - 1));
```
round up:
```c
val = (val - (WORD - 1) & ~(WORD - 1));
```
