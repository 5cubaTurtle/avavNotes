[cli-reference](https://docs.docker.com/engine/reference/commandline/docker/)
[nice short vid](https://youtu.be/J0NuOlA2xDc?si=2YlJYz7ie_cqZg5X)

A platform for building, shipping, and running [[Container|containers]], provides tools to manage containers. With Docker, developers can package their applications into containers, which can then be deployed consistently across different environments, from development to production.

The main purpose of docker is to reduce setup time of the environments where applications are ran and developed.

Check version: `docker --version`

> In the following commands, the place holders `<container>` or `<image>` can refers to the name or the ID of the element.

Build an image: `docker build -t welcome-to-docker .`
	`-t` flag tags your image with a name. (*welcome-to-docker* in this case).
	`.` lets Docker know where it can find the Dockerfile, (current directory "`.`" in this case).
List available [[image]]s: `docker images`
Delete an image: `docker rmi <image>` 
Run a container from an [[image]]: `docker run -p 4000:4000 <image>`
- `-p <port>` specify the port to communicate with the container.
List containers: `docker ps`
- `--no-trunc` Don't truncate output
List all containers: `docker container ls -a`
Stop container: `docker stop <container>`
Kill container: `docker kill <container>`
Push/Pull an image to [dockerhub](https://hub.docker.com/): `docker push`/`pull <image>`
Print logs of a container: `docker log <container>`
	Example: `docker logs -f --tail 200 webrunner`
- `-f` follow
- `--tail 200` show 200 last lines
Display system wide information: `docker system info`
Execute a command in a container: `docker exec -ti <container> bash`. Use this to open a terminal inside a container.
	- `-i`, `--interactive` Keep STDIN open even if not attached
	- `-t`, `--tty` Allocate a pseudo-TTY

### Space
[guide to free up space](https://docs.docker.com/desktop/faqs/linuxfaqs/#how-do-i-delete-unnecessary-containers-and-images)

If there are lots of redundant objects, run the command: `docker system prune`. This command removes all stopped containers, unused networks, dangling images, and build cache.
