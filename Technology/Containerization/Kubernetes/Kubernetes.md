- Kubernetes is an open-source [[container]] orchestration platform.
- Similar to [[Swarm]] but the industry standard.
- Automates the deployment, scaling, and management of containerized applications across clusters of machines.
- Provides features such as automatic scaling, self-healing, service discovery, and load balancing, making it easier to deploy and manage containerized applications at scale.
- It abstracts away the underlying infrastructure and provides a unified API to manage containerized workloads, regardless of the environment (on-premises, public cloud, or hybrid).
- Can schedule and orchestrate containers created with [[Docker]] but also supports other container runtimes such as containerd and CRI-O.

[Tutorials](https://kubernetes.io/docs/tutorials/)
[Installation guide](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-using-native-package-management), To use Kubernetes locally, also install [minikube](https://minikube.sigs.k8s.io/docs/start/).

### Usage
To start a local Kubernetes [[cluster]] for testing purposes use [[minikube]].
Get cluster info: `kubectl cluster-info`

Create a deployment: `kubectl create deployment myapplication --image=node`, here `myapplication` is the name of the deployment and `node` is the [[image]] to run.
	`--image=` could also be given a URL to the image. For example: `--image=http://google.com/node`.
Display deployments: `kubectl get deployments`
