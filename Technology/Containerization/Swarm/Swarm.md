Docker Swarm is a container orchestration tool built directly into [[Docker-Engine]]. It allows you to easily manage and deploy containerized applications across a cluster of multiple Docker hosts.

## Generated(Gemini) Overview
### What it does
- **Orchestrates containers:** Schedules and scales your containerized applications across a cluster of machines.
- **High availability:** Ensures your applications remain running even if individual machines fail.
- **Scaling:** Automatically scales your applications up or down based on demand.
- **Networking:** Provides built-in networking for your containers to communicate.
- **Service discovery:** Makes your services easily discoverable within the cluster.
- **Security:** Offers role-based access control and resource isolation.

### Key features
- **Swarm mode:** Enables container orchestration within Docker Engine.
- **Desired state reconciliation:** Ensures the cluster state matches your desired configuration.
- **Services:** Define how your application runs with replicas and resource specifications.
- **Stacks:** Group services together for easy deployment and management.
- **Networks:** Create isolated networks for your containerized applications.
- **Volumes:** Share data between containers across the cluster.

### Benefits
- **Simplified container management:** Easy to deploy and manage complex containerized applications.
- **Scalability:** Scales your applications horizontally as your needs grow.
- **High availability:** Provides fault tolerance and redundancy for your applications.
- **Flexibility:** Customizable to fit your specific needs and infrastructure.

### Comparison to alternatives
- **Simpler than Kubernetes:** Easier to set up and manage for smaller deployments.
- **Less feature-rich:** Lacks some advanced features of Kubernetes like multi-tenancy and advanced resource management.

### Who should use it
- Developers and DevOps teams deploying containerized applications.
- Businesses looking for a simple and scalable solution for container orchestration.

### For further learning
- **Docker Swarm Documentation:** [https://docs.docker.com/engine/swarm/](https://docs.docker.com/engine/swarm/)
- **Docker Swarm Tutorial:** [https://docs.docker.com/engine/swarm/swarm-tutorial/](https://docs.docker.com/engine/swarm/swarm-tutorial/)
- **Getting Started with Swarm mode:** [https://docs.docker.com/engine/swarm/](https://docs.docker.com/engine/swarm/)

## Usage
Initialize swarm: `docker swarm init`

Check if Swarm is enabled on your Docker Desktop by typing `docker system info`, and looking for a message *Swarm: active*.

```sh
docker swarm join --token SWMTKN-1-0mslwbxzmeynr25b9u0tiv0ftwy6opnmxfamc3grrard04dofk-dh6jfpccplc0254hfvrtt6e2y 192.168.65.9:2377
```

Info: `docker info`, then look at the Swarm section.

Seen list of [[node]]s: `docker node ls`
Deploy a [stack](https://docs.docker.com/engine/swarm/stack-deploy/) to a node: `docker stack deploy -c docker-compose.yml`
Create [[Technology/Containerization/Swarm/Service|Service]]: `docker service create --replicas 1 --name nodeserver2 node ping docker.com`
