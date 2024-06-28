---
aliases:
  - addgroup
---
#linux
`adduser`, `addgroup` - Add a user or a group to the system
Wrapper scripts for [[useradd]], [[groupadd]] and [[usermod]].

In Fedora linux:
Add user named "jay": `adduser -m -g users -G wheel jay`
- `-m` add home directory 
- `-g` set primary group
- `-G` set secondary group (notice in Fedora will is the *sudo* group equivalent)

Remember to also create a [[passwd|password]] for the user.

In Ubuntu:
Add user named "jay": `adduser jay`

Use [[usermod]] to make the user a sudoer