Instructions for the image creation:

**FROM** *baseImage*
	The name of the base image to use. Set the base image to use for any subsequent instructions that follow.

**WORKDIR**
	The absolute or relative path to use as the working directory. Will be created if not present. Set the working directory for any ADD, COPY, CMD, ENTRYPOINT, or RUN instructions that follow.

**ENV** key value
	Set an environment variable to the specified value. The value will be in the environment of any descendant Dockerfiles.

**COPY** [flags] source ... *dest*
	The resource to copy. Copy new files and directories to the image's filesystem.

**RUN** *command* parameter
	A parameter to the command. Execute commands inside a shell.

**EXPOSE** *port* ...
	The port that this container should listen on. Define network port for this container to listen on at runtime.

**CMD** [ "executable", "parameter", ...]
	Set the default executable and parameters for this executing container.

### Example file
```Dockerfile
FROM node
WORKDIR /client
COPY package*.json ./
RUN npm install
COPY . /client/
EXPOSE 3000
CMD [ "npm", "start"]
```

A Dockerfile is a text file containing instructions to build a Docker [[image]]. Each instruction builds upon the previous one, creating layers within the image.

### Basic Structure
- **Syntax version:** Optionally specify the Dockerfile syntax version with `# syntax=docker/dockerfile:1`.
- **Instructions:** Each line is an instruction followed by arguments (e.g., `FROM ubuntu:20.04`).
- **Comments:** Start lines with `#` for comments (ignored during build).

### Key Instructions
- **FROM:** Defines the base image (e.g., `ubuntu:20.04`).
- **MAINTAINER:** Provides author information (optional).
- **RUN:** Executes shell commands and commits changes (e.g., `RUN apt update && apt install -y nginx`).
- **COPY/ADD:** Copies files/directories from build context to the image (e.g., `COPY ./app /app`).
- **ENV:** Sets environment variables (e.g., `ENV PORT=80`).
- **ENTRYPOINT/CMD:** Specifies the default command to run in the container.
- **EXPOSE:** Makes specific ports accessible from outside the container (e.g., `EXPOSE 80`).
- **VOLUME:** Defines directories shared between container and host machine.
- **WORKDIR:** Sets the working directory within the container.
- **USER:** Sets the user within the container (e.g., `USER nginx`).
- **ARG:** Defines build-time variables used in instructions.

### Additional Points
- Instructions are case-sensitive.
- Arguments are space-separated.
- Use backslashes (`\`) to escape special characters.
- Multi-line commands use backslashes to continue (e.g., `RUN \ apt update \ && apt install -y nginx`).

### Resources
- **Dockerfile reference:** [https://docs.docker.com/engine/reference/builder/](https://gemini.google.com/%3C0%3Ehttps://docs.docker.com/engine/reference/builder/)
- **Best practices for writing Dockerfiles:** [https://docs.docker.com/develop/develop-images/dockerfile_best-practices/](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

### COPY vs ADD
|Feature|COPY|ADD|
|---|---|---|
|Source |Local files/directories|Local files/directories, URLs|
|Tar extraction|No|Auto-extracts .tar archives|
|Compression|No|Unpacks gzip, bzip2, xz|
|Best Practices|Preferred option|Use only for specific needs|
Using `ADD` for remote URLs is typically discouraged as it increases image size unnecessarily. Use alternative methods like `curl` to download and manage remote files instead.
