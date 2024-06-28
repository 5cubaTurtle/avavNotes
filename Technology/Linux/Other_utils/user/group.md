#linux 
A collection of user accounts that share certain permissions and privileges on the system.
### Purpose
1. **Access Control**: Groups are used to control access to files and directories by assigning permissions to group members. This allows administrators to grant or restrict access to specific resources based on group membership.
2. **Collaboration**: Groups facilitate collaboration by allowing multiple users to work on shared files or projects with a common set of permissions.
3. **Administrative Privileges**: Groups can be used to grant administrative privileges to specific users, allowing them to perform certain administrative tasks on the system.
### Managing Groups
By assigning appropriate group ownership and permissions, administrators can control access to files and directories based on group membership.
#### Files
1. **`/etc/group` File**: This file contains a list of all the groups on the system, along with their group IDs (GIDs) and member usernames. Administrators can manually edit this file to create, modify, or delete groups.
2. **`/etc/gshadow` File**: This file stores encrypted group passwords and other group-related security information. It is only accessible by the root user.
3. **`/etc/group` Directory**: Some distributions may use a directory structure (`/etc/group.d/`) to manage groups, with each group having its own separate file.
#### Commands
4.  [[groupadd]]: create new groups on the system.
5. [[groupdel]]:  delete groups from the system.
6. [[groupmod]]: modify group properties, such as the group name or GID.
7. [[usermod]]: add or remove users from groups.
### Group Types
1. **Primary Group**: Each user account is associated with a primary group, which is specified in the `/etc/passwd` file. This is the default group that a user belongs to when creating files or directories.
2. **Supplementary Group**: Users can also belong to one or more supplementary groups, which are additional groups that grant them extra permissions beyond those provided by their primary group.