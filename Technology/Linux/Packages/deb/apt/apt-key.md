APT key management utility, used to manage the list of keys used by apt to authenticate packages. Packages which have been authenticated using these keys will be considered trusted.

Import the MongoDB public GPG key:
```sh
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```

List added keys:`sudo apt-key list`
