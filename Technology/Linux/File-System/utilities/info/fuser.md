identify processes using files or sockets

fuser  displays  the PIDs of processes using the specified files or file systems.  In the default display mode, each file name is followed by a letter denoting the type of access:

`c`      current directory.
`e`      executable being run.
`f`      open file.  f is omitted in default display mode.
`F`      open file for writing.  F is omitted in default display mode.
`r`      root directory.
`m`      mmap'ed file or shared library.
`.`      Placeholder, omitted in default display mode.

check who is using the video device 0: `fuser /dev/video0`