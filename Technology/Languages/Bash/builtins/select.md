#bash #shell #menu
The `select` construct allows you to generate menus.

[linuxize tutorial](https://linuxize.com/post/bash-select/)
A custom prompt for the `select` construct can be set using the `PS3`  .

syntax:
```shell
select i in ${robots[@]}
do
...
done
```