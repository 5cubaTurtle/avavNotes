[guide](https://phoenixnap.com/kb/how-to-install-python-3-ubuntu#ftoc-heading-15)
Installing via [Personal Package Archive (PPA)](https://phoenixnap.com/glossary/personal-package-archive):
```sh
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.12
python3 --version
```
These commands include [[add-apt-repository|adding]] *deadsnakes* repository to [[apt]] local [[sources.list]].
Last line verifies the installed version.
