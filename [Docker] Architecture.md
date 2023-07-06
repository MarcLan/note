# Docker Architecture

## Docker architecture

### Docker consists of three basic concepts:

- **Image:** A Docker image is equivalent to a root file system. For example, the official image ubuntu:16.04 contains a complete root file system of the minimum system of Ubuntu16.04.
- **Container:** The relationship between image and container is just like classes and instances in object-oriented programming. Mirror is a static definition, and container is an entity when mirroring is running. Containers can be created, started, stopped, deleted, paused, etc.
- **Repository:** The repository can be regarded as a code control center for storing images.

Docker uses a client-server (C/S) architecture pattern and uses a remote API to manage and create Docker containers. Docker containers are created from Docker images. The relationship between containers and images is similar to objects and classes in object-oriented programming.

| Docker    | object oriented |
| :-------- | :-------------- |
| container | object          |
| image     | class           |

![image-20230706164307479](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230706164307479.png)

| Concept         | Description                                                  |
| :-------------- | :----------------------------------------------------------- |
| Images          | A Docker image is a template for creating Docker containers, such as an Ubuntu system. |
| Container       | A container is an application or a group of applications that run independently, and is the entity of the image runtime. |
| Client          | The Docker client communicates with the Docker daemon through the command line or other tools using the Docker SDK (https://docs.docker.com/develop/sdk/). |
| Host            | A physical or virtual machine used to execute the Docker daemon and containers. |
| Docker Registry | The Docker warehouse is used to store images, which can be understood as a code warehouse in code control. Docker Hub (https://hub.docker.com) provides a huge collection of images for use. A Docker Registry can contain multiple warehouses (Repository); each warehouse can contain multiple tags (Tag); each tag corresponds to a mirror. Usually, a warehouse will contain images of different versions of the same software, and tags are often used to correspond to each version of the software. We can use the format of <warehouse name>:<label> to specify which version of the software is the mirror image. If no tag is given, latest will be used as the default tag. |
| Docker Machine  | Docker Machine is a command-line tool that simplifies Docker installation. Docker can be installed on corresponding platforms through a simple command line, such as VirtualBox, Digital Ocean, and Microsoft Azure. |