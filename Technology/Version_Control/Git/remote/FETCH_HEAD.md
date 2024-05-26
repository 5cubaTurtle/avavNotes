#git 
[from StckOvrflw](https://stackoverflow.com/a/9237511/5273667)

This is the pointer to the tip of the recently [[fetch]]ed branch. If you ran [[fetch]] instead of [[pull]], there will be difference in commits between [[Technology/Version_Control/Git/miscellaneous/HEAD|HEAD]] and FETCH_HEAD.
To see this difference in logs: `git log FETCH_HEAD`
To merge the current branch to the fetched commits from the remote, run:`git merge FETCH_HEAD`
