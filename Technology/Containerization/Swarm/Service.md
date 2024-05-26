[doc](https://docs.docker.com/engine/swarm/key-concepts/#services-and-tasks)
"A service is the definition of the tasks to execute on the manager or worker nodes. It is the central structure of the swarm system and the primary root of user interaction with the swarm."

List services: `docker service ls`
Create Service: `docker service create --replicas 1 --name nodeserver2 <image>`
	- `--replicas` is the number of workers.
	-  `--name` is the name of the service
	- `<image>` could be pulled from the web for example: `node ping docker.com`