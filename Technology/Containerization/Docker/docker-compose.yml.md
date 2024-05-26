[doc](https://docs.docker.com/compose/compose-application-model/)

The name of the configuration file should be *docker-compose.yml*.
Example file:
```yaml
version: "1"
services:
    app:
        container_name: app
        restart: always
        build: .
        ports:
            - "4000:4000"
        links:
            - mongo

    mongo:
        container_name: mongo
        image: mongo
        volumes:
            - ./data:/data/db
        ports:
            - "27017:27017"

```