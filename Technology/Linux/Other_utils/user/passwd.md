#linux 
change user password

change a password for a user:`sudo passwd reprepro`. The changing user has to be sudoer.

### /etc/passwd
Each entry in the `/etc/passwd` file represents a user account on a Linux system. Each line in the file contains several fields separated by colons (`:`). Here is the meaning of each field:

1. Username: This field contains the username of the user.
2. Password: Historically, the password field used to store an encrypted password. However, modern Linux systems store a placeholder character (`x` or `*`) in this field, indicating that the actual password is stored in the `/etc/shadow` file or another authentication mechanism.
3. User ID (UID): This field contains the numeric user ID assigned to the user. The UID 0 represents the root user.
4. Group ID (GID): This field indicates the primary group ID assigned to the user. It corresponds to the GID in the `/etc/group` file.
5. User Information: This field typically contains additional information about the user, such as their full name or a description.
6. Home Directory: This field specifies the path to the user's home directory, where they typically store their files and configurations.
7. Shell: This field indicates the default shell assigned to the user. It determines the command interpreter used when the user logs in.

Additional fields or customizations may exist in certain Linux distributions or setups, but the above fields are the standard ones found in the `/etc/passwd` file.