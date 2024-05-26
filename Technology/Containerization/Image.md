Image serves as a template or blueprint for creating container instances.

[[Container]] images are often built using [[Dockerfile]]s, which are text files that contain a series of instructions for assembling the image layers. These instructions specify the base image, copy application code and dependencies, configure environment variables, and set up the runtime environment.

Once an image is built, it can be stored in a container registry, such as Docker Hub or a private registry, where it can be versioned, shared, and reused by others. When a container is launched from an image, it runs in isolation from other containers and shares the host operating system kernel, making it lightweight and efficient.

Every image has an ID: *IMAGE ID*
