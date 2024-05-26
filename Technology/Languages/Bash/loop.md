#bash 

#### for loop
From [SO](https://stackoverflow.com/questions/10523415/execute-command-on-all-files-in-a-directory)
The following bash code will pass $file to command where $file will represent every file in /dir
```shell
for file in /dir/*
do
  cmd [option] "$file" >> results.out
done
```

oneliner:
```shell
el@defiant ~/foo $ touch foo.txt bar.txt baz.txt
el@defiant ~/foo $ for i in *.txt; do echo "hello $i"; done
hello bar.txt
hello baz.txt
hello foo.txt
```

#### range:
print 1 to 10:   `echo {1..10}`
print a to z:   `echo {a..z}`

run over a list:
```shell
repos=(  
    $HOME/catkin_ws/src/llc_ubuntu  
    $HOME/catkin_ws/src/core_autonomy  
    $HOME/catkin_ws/llc_arduino  
)
  
for repo in ${repos[*]}; do  
    cd $repo || exit 4  
done
```

loop with a condition:
```bash
for ((i=4; i && (! ls); i--)); do
    echo "i:$((i-1))"
done
```
