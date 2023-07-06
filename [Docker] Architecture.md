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

![image-20230706165743863](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230706165743863.png)