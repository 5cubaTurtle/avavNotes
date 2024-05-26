
counter for bits which are 'on':

This function counts the number of bits with value of *1*. Number of operation depends on number of bits which are on.
```c
int count_on_bits(unsigned int num) {
    int counter = 1;
    if(!num)
		return 0;

    while (num &= (num-1))
		++counter;
    return counter;
}
```

Count adjacent pairs of on bits:
```c
int count_pairs(unsigned int num) {
	return count_on_bits(num & num<<1);
}
```