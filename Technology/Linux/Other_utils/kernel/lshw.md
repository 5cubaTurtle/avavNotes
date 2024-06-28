#linux 
list hardware

see manufacturer: `sudo lshw|grep product` or `sudo lshw -c system`
- `-c, -class` list a specific class (see classes with `lshw -short`)
network card/s info: `sudo lshw -c network`

GPU info: ` sudo lshw -C display ` alternatively use [[chrome]] at url: chrome://gpu/