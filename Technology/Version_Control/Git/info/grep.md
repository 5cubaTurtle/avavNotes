#git 
Print lines matching a pattern in the tracked files

git-grep usage is similar to standard linux utility [[Technology/Linux/utils/Search/grep|grep]], however, it could only be run from within a git repo and it excludes the untracked files.

find all strings "30" in find confing/SWconfig.json: ``git grep 30 config/SWconfig.json
