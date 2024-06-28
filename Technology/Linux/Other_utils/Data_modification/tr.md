#stream 
translate or delete characters

splitting $PATH into several lines by the ':' delimiter: `echo $PATH | tr : \\n` 
splitting by several delimiters: `cat calibration.json |tr {, \\n`
uppercase text of a 🗃️: `cat file | tr [a-z] [A-Z]`
Delete all letters from a file: `cat file.txt | tr -d [:alpha:]`
