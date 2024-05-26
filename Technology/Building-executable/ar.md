create, modify, and extract from archives.
### syntax (simplified):
`ar [-]p[mod] archive [member]`
- **mod** is  modifier letter. it modifies the command **p**
##### Create library "libctest.a":
`ar -cvq libctest.a ctest1.o ctest2.o`
flags:
- `c` (**mod**) Create the archive. (suppresses a warning)
- `v` (**p**) verbose
- `q` (**p**) Quick append; Historically, add the files **member**... to the end of **archive**, without checking for replacement.
##### Create archive file using object file:
`ar rcs library.a code.o`
- `r` (**p**) Insert the files **member**... into **archive** (with _replacement_). This operation differs from q in that any previously existing members are deleted if their names match those being added.
- `s` (**p**) Add index-table to the archive, or update it if it already exists.
### List files in library:
Display contents of archive: `ar -t libctest.a`
