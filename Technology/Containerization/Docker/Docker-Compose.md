[docs](https://docs.docker.com/compose/)
[cli-reference](https://docs.docker.com/compose/reference/)
`docker compose --help` will print the help menu

A tool for defining and running multi-container applications; manage services, networks, and volumes in a single, comprehensible YAML [[Docker-Compose|configuration]] file. Then, with a single command, you create and start all the services from your configuration file.

Check version: `docker compose version`
Build/rebuild services: `docker compose build`
Create and start containers: `docker compose up <service>`, if no service provided, all services from the [[docker-compose.yml]] file will be started.
	`-d` or `--detached` will run the containers in the background.
Stop containers: `docker compose stop`
List containers: `docker compose ps`