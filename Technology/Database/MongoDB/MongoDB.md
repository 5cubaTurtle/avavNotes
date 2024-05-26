[official guide](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/) for installing on ubuntu.

Check connection status to the DB server:
```sh
mongo --eval 'db.runCommand({ connectionStatus: 1 })'
```

Start the [`mongod`](https://www.mongodb.com/docs/manual/reference/program/mongod/#mongodb-binary-bin.mongod) process: `sudo systemctl start mongod`
Restart: `sudo systemctl restart mongod`

### Remote access
[Remote access to the DB guide](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#additional-information)
### Configuration
MongoDB package includes a [configuration file](https://www.mongodb.com/docs/manual/reference/configuration-options/#std-label-conf-file) (`/etc/mongod.conf`)
These settings (such as the data directory and log directory specifications) take effect upon startup. That is, if you change the configuration file while the MongoDB instance is running, you must restart the instance for the changes to take effect.

### Uninstalling
[ubuntu uninstalling guide](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#uninstall-mongodb-community-edition)
