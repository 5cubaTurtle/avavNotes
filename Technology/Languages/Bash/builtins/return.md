useful for stopping execution of a function w/o exiting the whole script or shell:
```sh
[[ -z $ROBOT ]] && { echo "set ROBOT first via one of the aliases"; return 1; }
...
# more logic here
...
```
