From [docs](https://docs.docker.com/desktop/):
"GUI environment that lets you build, share, and run containerized applications and [[microservice]]s. It takes care of port mappings, file system concerns, and other default settings."

Start the docker-desktop through cli:
```shell
systemctl --user start docker-desktop
```

Check version: `docker version`

To [[systemctl|enable]] Docker Desktop to start on sign-in:
```sh
systemctl --user enable docker-desktop.service
```
To stop the service: `systemctl --user stop docker-desktop.service`

To open the learning center click the graduate cap at the right top corner:
![[Learning-Center-Icon.png]]
