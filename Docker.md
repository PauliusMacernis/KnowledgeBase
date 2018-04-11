 ## Docker
 
- **What is Docker?**  
Docker is a computer program that performs operating-system-level virtualization also known as containerization. It is developed by Docker, Inc. Docker is primarily developed for Linux, where it uses the resource isolation features of the Linux kernel such as cgroups and kernel namespaces, and a union-capable file system such as OverlayFS and others to allow independent "containers" to run within a single Linux instance, avoiding the overhead of starting and maintaining virtual machines (VMs).The Linux kernel's support for namespaces mostly isolates an application's view of the operating environment, including process trees, network, user IDs and mounted file systems, while the kernel's cgroups provide resource limiting for memory and CPU. Since version 0.9, Docker includes the libcontainer library as its own way to directly use virtualization facilities provided by the Linux kernel, in addition to using abstracted virtualization interfaces via libvirt, LXC and systemd-nspawn.  
When people say “Docker” they typically mean Docker Engine, the client-server application made up of the Docker daemon, a REST API that specifies interfaces for interacting with the daemon, and a command line interface (CLI) client that talks to the daemon (through the REST API wrapper).  
Read more:  
https://en.wikipedia.org/wiki/Docker_(software)  
https://www.docker.com/what-docker  
https://docs.docker.com/machine/overview/#whats-the-difference-between-docker-engine-and-docker-machine  
 
- **What is Docker Compose (`docker-compose`)?**  
Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.  
Using Compose is basically a three-step process:  
  1. Define your app’s environment with a `Dockerfile` so it can be reproduced anywhere.
  2. Define the services that make up your app in `docker-compose.yml` so they can be run together in an isolated environment.  
  3. Run `docker-compose up` and Compose starts and runs your entire app.  
  
  Read more:  
  https://docs.docker.com/compose/overview/  

- **What is Docker Machine (`docker-machine`)?**  
Docker Machine is a tool that lets you install Docker Engine on virtual hosts, and manage the hosts with `docker-machine` commands. You can use Machine to create Docker hosts on your local Mac or Windows box, on your company network, in your data center, or on cloud providers like Azure, AWS, or Digital Ocean.  
Using `docker-machine` commands, you can start, inspect, stop, and restart a managed host, upgrade the Docker client and daemon, and configure a Docker client to talk to your host.  
Point the Machine CLI at a running, managed host, and you can run docker commands directly on that host. For example, run `docker-machine env default` to point to a host called `default`, follow on-screen instructions to complete `env` setup, and run `docker ps`, `docker run hello-world`, and so forth.  
Read more:  
https://docs.docker.com/machine/overview/  
 
- **What is the difference between using `docker run` and `docker-machine start`?**  
Docker Engine accepts docker commands from the CLI, such as `docker run <image>`, `docker ps` to list running containers, `docker image ls` to list images, and so on.  
Docker Machine is a tool for provisioning and managing your Dockerized hosts (hosts with Docker Engine on them). Typically, you install Docker Machine on your local system. Docker Machine has its own command line client `docker-machine` and the Docker Engine client, `docker`. You can use Machine to install Docker Engine on one or more virtual systems. These virtual systems can be local (as when you use Machine to install and run Docker Engine in VirtualBox on Mac or Windows) or remote (as when you use Machine to provision Dockerized hosts on cloud providers). The Dockerized hosts themselves can be thought of, and are sometimes referred to as, managed “machines”.   
Docker runs processes in isolated containers. A container is a process which runs on a host. The host may be local or remote. When an operator executes `docker run`, the container process that runs is isolated in that it has its own file system, its own networking, and its own isolated process tree separate from the host.  
The basic docker run command takes this form: `docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]`  
The basic docker-machine start command takes this form: `docker-machine start [arg...]`. It starts a machine, argument(s) are one or more machine names.  
Read more:  
https://docs.docker.com/machine/overview/  
https://docs.docker.com/machine/reference/start/  
https://docs.docker.com/engine/reference/run/  


- **What is storage driver for? For example, `overlay2`, `aufs`**  
Storage drivers allow us to create data in the writable layer of our container. The files won’t be persisted after the container stops, and both read and write speeds are low.  
A Docker image is built up from a series of layers. Each layer represents an instruction in the image’s Dockerfile. Each layer except the very last one is read-only. Consider the following Dockerfile:  
```
FROM ubuntu:15.04
COPY . /app
RUN make /app
CMD python /app/app.py

```
This Dockerfile contains four commands, each of which creates a layer.  
Each layer is only a set of differences from the layer before it. The layers are stacked on top of each other. When we create a new container, we add a new writable layer on top of the underlying layers. This layer is often called the “container layer”. All changes made to the running container, such as writing new files, modifying existing files, and deleting files, are written to this thin writable container layer.  
A storage driver handles the details about the way these layers interact with each other. Different storage drivers are available, which have advantages and disadvantages in different situations.  
Read more:  
https://docs.docker.com/storage/storagedriver/

- **What is the difference between a container and an image?**  
The major difference between a container and an image is the top writable layer. All writes to the container that add new or modify existing data are stored in this writable layer. When the container is deleted, the writable layer is also deleted. The underlying image remains unchanged.  
Because each container has its own writable container layer, and all changes are stored in this container layer, multiple containers can share access to the same underlying image and yet have their own data state.   
Docker uses storage drivers to manage the contents of the image layers and the writable container layer. Each storage driver handles the implementation differently, but all drivers use `stackable image layers` and the `copy-on-write` (`CoW`) strategy.
Read more:  
https://docs.docker.com/storage/storagedriver/#container-and-layers  

- **What is the difference between `overlay2` and `aufs` storage engines?**  
`AUFS` is a `union` filesystem. The `aufs` storage driver was previously the default storage driver used for managing images and layers on Docker for Ubuntu, and for Debian versions prior to Stretch.  
`AUFS` is not supported on some distributions and Docker editions.  
If the installed Linux kernel is version 4.0 or higher, and we use Docker CE, consider using the newer `overlay2`, which has potential performance advantages over the `aufs` storage driver. For version 3 of the Linux kernel, aufs is supported because `overlay` or `overlay2` drivers are not supported by that kernel version.  
Read more:  
https://docs.docker.com/storage/storagedriver/select-storage-driver/  
https://docs.docker.com/storage/storagedriver/aufs-driver/  

- **What does `sudo docker run hello-world` command do?**  
This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.  

- **What does `sudo dockerd` command do?**  
It manualy runs Docker daemon. When you start Docker this way, it runs in the foreground and sends its logs directly to your terminal. `Ctrl`+`C` will stop the deamon.  
Most often Docker deamon is configured to start automatically at system boot but starting it manualy is also the option.  

- **What does `dockerd --help` command do?**  
Thsi will show more info (help) on Docker deamon. The list of all Docker deamon configuration options may be found in the output of the command.

- **What does `docker images` command do?**  
Lists local images.  
The default `docker images` will show all top level images, their repository and tags, and their size.  
Docker images have intermediate layers that increase reusability, decrease disk usage, and speed up docker build by allowing each step to be cached. These intermediate layers are not shown by default.  
The SIZE is the cumulative space taken up by the image and all its parent images. This is also the disk space used by the contents of the Tar file created when you docker save an image.  
An image will be listed more than once if it has multiple repository names or tags. This single image (identifiable by its matching IMAGE ID) uses up the SIZE listed only once.
Usage: `docker images [OPTIONS] [REPOSITORY[:TAG]]`  

- **What does `docker rmi` command do?**  
Remove one or more local images.  
Usage: `docker rmi [OPTIONS] IMAGE [IMAGE...]`,  
Another example: `docker rmi <hash>` where `<hash>` is the `IMAGE ID` from the result of `docker images`.





