Docker is an open-source platform for developing, delivering, and running applications.
It is based on the idea of software containers.

- makes easier to detach applications from infrastructure
- hortens the time between code creation and deployment

**Containers**
The code, libraries, system tools, and configurations required to run an application are all included in these self-contained containers .

 Developers can use Docker to generate a container image that contains the application code together with all of its dependencies (particular libraries and versions of Python) and any setups that the system may require.

 This saves developers a great deal of time and work because it not only makes deployment simpler but also ensures consistent behavior across all settings.

Docker integration is offered by cloud providers


Why ?
1. Consistency
ensure my app run same across different environment and operating system .

2. One command Setup 
without docker we need to setup individual services in order .
3. Easy to set up

**Docker Containers vs Virtual Machines**


**Docker daemon/dockerd**
Docker daemon builds, manages, and distributes your Docker containers.

**Docker Architecture**
- Docker uses a client-server architecture.
-  The Docker client communicates with the Docker daemon.


**Docker Hub**
- Docker Hub is a cloud-based repository service that allows users to store, share, and manage Docker container images.
- It is offered by Docker

Docker Image
- A text file known as a Dockerfile forms the basis of a Docker image
-  The instructions for creating the image layer by layer are contained in this file.
- Docker images are read-only templates, so any changes you make to the running program happen inside a container, not to the image itself.



- Docker images consist of several layers.

Tagging
- A repository name and a tag combine to form a unique identification for Docker images.
- Tags are used to distinguish between various image versions.
- 

DOckerFile
- By specifying the build process in a Dockerfile, you can automate and replicate the image creation process, assuring consistency across environments.


Why docker so Fast ?
- Docker uses layer caching while building images.
- When you construct an image, Docker leverages previously built cached layers if the associated Dockerfile instructions haven't changed.
- This drastically cuts down on build times, particularly for big projects with complex dependencies.