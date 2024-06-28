#linux #networking 
get entries from Name Service Switch libraries

see all hosts in /etc/hosts:   `getent hosts`
ip of a hostname:   `getent hosts <hostname>`

to print a comprehensive list of all users: `getent passwd | awk -F: '{ print $1 }'`
