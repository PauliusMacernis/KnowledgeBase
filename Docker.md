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
```
Options:
  -a, --all             Show all images (default hides intermediate images)
      --digests         Show digests
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print images using a Go template
      --no-trunc        Don't truncate output
  -q, --quiet           Only show numeric IDs
```

- **What does `docker rmi` command do?**  
Remove one or more images.  
Usage: `docker rmi [OPTIONS] IMAGE [IMAGE...]`,  
Another example: `docker rmi <hash>` where `<hash>` is the `IMAGE ID` from the result of `docker images`.  
It is also possible to remove images by name:tag, for example: `docker rmi php:latest`.  
```
Options:
  -f, --force      Force removal of the image
      --no-prune   Do not delete untagged parents
```

- **What does `docker rm` command do?**  
Remove one or more containers.  
Usage: `docker rm [OPTIONS] CONTAINER [CONTAINER...]`,  
Another example: `docker rm <hash>` where `<hash>` is the `CONTAINER ID` from the result of `docker ps -a`.  
```
Options:
  -f, --force     Force the removal of a running container (uses SIGKILL)
  -l, --link      Remove the specified link
  -v, --volumes   Remove the volumes associated with the container
```

- **Can a Docker image be removed if it is being used by the stopped Docker container?**  
No. The image cannot be removed while it is being used by container. At first we need to remove the container (`docker rmi <container_hash>`) then the image may be removed.  

- **What does `docker ps -a` command do?**  
It lists running Docker containers. Option `-a` tells to list all containers - both currently running and stopped.  
```
Options:
  -a, --all             Show all containers (default shows just running)
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print containers using a Go template
  -n, --last int        Show n last created containers (includes all
                        states) (default -1)
  -l, --latest          Show the latest created container (includes all
                        states)
      --no-trunc        Don't truncate output
  -q, --quiet           Only display numeric IDs
  -s, --size            Display total file sizes
```

- **What is the difference between `docker images` as `docker ps -a`?**  
`docker images` is for all Docker images to list, `docker ps -a` is for all Docker containers to list.  

- **Which command should be used to remove the container and which to remove the image?**  
`docker rm <hash>` will remove the container, `docker rmi <hash>` will remove an image. Image cannot be removed while any containers using the image exist.  
  
- **What is https://hub.docker.com for?**  
It is the place in where Docker images are listed in the form of official repositories. For example, PHP official repository - https://hub.docker.com/_/php/  

- **What is `Dockerfile`?**  
This file is a set of instructions that define building images, each step creating a new layer on top of the previous. The new layers are created for the same and for the different instructions, for example, `RUN touch /tmp/foo` and `RUN touch /tmp/bar` would create not one but two different layers while `RUN touch /tmp/foo && touch /tmp/bar` would create one only.
Docker can build images automatically by reading the instructions from a `Dockerfile`. A `Dockerfile` is a text document that contains all the commands a user could call on the command line to assemble an image. Using `docker build` users can create an automated build that executes several command-line instructions in succession.  
Read more:  
https://docs.docker.com/engine/reference/builder/  

- **Explain `docker build -t phpinfo .`**  
The `build` command has a `-t` flag, which tags the image as `phpinfo`, and the last argument (`.`) is the path where Docker will look for our files.  

- **Explain `docker run -p 8080:80 -d --name=my-phpinfo phpinfo`**  
The `run` command runs a container with the tagged `phpinfo` image.  
The `-p` flag maps port `8080` on the local machine to port `80` in the container, which means that we'll use port `8080` locally to access our application.  
The `--name` flag assigns a name to the running container that we can use to issue further commands, like `docker stop my-phpinfo`. If we don't provide a name, Docker creates a random auto-generated name for us.  
The `-d` flag (detach) is used to run the container in the background. Without the `-d` flag Docker runs in the foreground.  

- **Explain `docker start [OPTIONS] CONTAINER [CONTAINER...]`**  
The command starts one or more stopped containers.  
Read more: https://docs.docker.com/engine/reference/commandline/start/  
```
Options:
Name             shorthand  Description
--attach         -a         Attach STDOUT/STDERR and forward signals
--checkpoint                experimental (daemon) Restore from this checkpoint
--checkpoint-dir            experimental (daemon) Use a custom checkpoint storage directory
--detach-keys               Override the key sequence for detaching a container
--interactive    -i         Attach container’s STDIN
```

- **Explain `docker stop [OPTIONS] CONTAINER [CONTAINER...]`**  
The command stops one or more running containers.  
Read more: https://docs.docker.com/engine/reference/commandline/stop/  
```
Options:
Name,    shorthand  Default  Description
--time   -t         10       Seconds to wait for stop before killing it
```

- **Explain the following content of docker-compose.yml:**  
```
version: "3"
services:
  phpinfo:
    build: .
    ports:
      - "8080:80"
```

The `services` key defines one service called `phpinfo`.  
Inside the `phpinfo` service, the `build` key references a dot (`.`), which means we expect the `Dockerfile` in the current path (`.`). Lastly, the `ports` key contains an array of port maps from the host server, just like `docker run -p 8080:80`. The port format is: `<host_port>:<container_port>`, which in our case means that port `8080` on the local machine will map to port `80` inside the container.  
We are using version `3` (https://docs.docker.com/compose/compose-file/), which is the recommended version at the time of writing.  

- **Explain `docker-compose up -d --build`**  
The command builds, (re)creates, starts, and attaches to containers for a service.  
Unless they are already running, this command also starts any linked services.  
The `docker-compose up` command aggregates the output of each container (essentially running `docker-compose logs -f`). When the command exits, all containers are stopped. Running `docker-compose up -d` starts the containers in the background and leaves them running.  
The `--build` option is for building images before starting containers.  
More info: https://docs.docker.com/compose/reference/up/  
```
Usage: up [options] [--scale SERVICE=NUM...] [SERVICE...]

Options:
    -d, --detach               Detached mode: Run containers in the background,
                               print new container names. Incompatible with
                               --abort-on-container-exit.
    --no-color                 Produce monochrome output.
    --quiet-pull               Pull without printing progress information
    --no-deps                  Don't start linked services.
    --force-recreate           Recreate containers even if their configuration
                               and image haven't changed.
    --always-recreate-deps     Recreate dependent containers.
                               Incompatible with --no-recreate.
    --no-recreate              If containers already exist, don't recreate
                               them. Incompatible with --force-recreate and -V.
    --no-build                 Don't build an image, even if it's missing.
    --no-start                 Don't start the services after creating them.
    --build                    Build images before starting containers.
    --abort-on-container-exit  Stops all containers if any container was
                               stopped. Incompatible with -d.
    -t, --timeout TIMEOUT      Use this timeout in seconds for container
                               shutdown when attached or when containers are
                               already running. (default: 10)
    -V, --renew-anon-volumes   Recreate anonymous volumes instead of retrieving
                               data from the previous containers.
    --remove-orphans           Remove containers for services not defined
                               in the Compose file.
    --exit-code-from SERVICE   Return the exit code of the selected service
                               container. Implies --abort-on-container-exit.
    --scale SERVICE=NUM        Scale SERVICE to NUM instances. Overrides the
                               `scale` setting in the Compose file if present.

```

- **Explain `docker-compose stop`**  
Stops running containers without removing them. They can be started again with `docker-compose start`.  
```
Usage: stop [options] [SERVICE...]

Options:
-t, --timeout TIMEOUT      Specify a shutdown timeout in seconds (default: 10).
```

- **Explain `docker-compose stop && docker-compose rm`**  
Remove stopped containers.  

- **Explain `docker-compose ps`**  
List running containers that Docker Compose is managing.  
https://docs.docker.com/compose/reference/ps/
```
Usage: ps [options] [SERVICE...]

Options:
-q    Only display IDs
```

- **Explain `docker-compose restart`**  
Restarts all stopped and running containers (services).  
If you make changes to your `docker-compose.yml` configuration these changes are not reflected after running this command.  
For example, changes to environment variables (which are added after a container is built, but before the container’s command is executed) are not updated after restarting.  
```
Usage: restart [options] [SERVICE...]

Options:
-t, --timeout TIMEOUT      Specify a shutdown timeout in seconds. (default: 10)
```

- **Explain `docker-compose restart phpinfo`**  
Restart a specific container matching the service key in `docker-compose.yml`.  


- **Explain `docker-compose down`**  
Stops containers and removes containers, networks, volumes, and images created by `up`.  
By default, the only things removed are: 
    - Containers for services defined in the Compose file  
    - Networks defined in the networks section of the Compose file  
    - The default network, if one is used  

Networks and volumes defined as external are never removed.  
More info: https://docs.docker.com/compose/reference/down/
```
Usage: down [options]

Options:
    --rmi type              Remove images. Type must be one of:
                              'all': Remove all images used by any service.
                              'local': Remove only images that don't have a
                              custom tag set by the `image` field.
    -v, --volumes           Remove named volumes declared in the `volumes`
                            section of the Compose file and anonymous volumes
                            attached to containers.
    --remove-orphans        Remove containers for services not defined in the
                            Compose file
    -t, --timeout TIMEOUT   Specify a shutdown timeout in seconds.
                            (default: 10)
```

- **Explain `docker-compose down --volumes`**  
Remove named volumes.  

- **Explain `docker exec -it c9a517f6f751 bash`**  
Runs a command in a running container.  
Usage: `docker exec [OPTIONS] CONTAINER COMMAND [ARG...]`  
```
Options
Name          shorthand  Default  Description
--detach      -d                  Detached mode: run command in the background
--detach-keys                     Override the key sequence for detaching a container
--env         -e                  API 1.25+: Set environment variables
--interactive -i                  Keep STDIN open even if not attached
--privileged                      Give extended privileges to the command
--tty         -t                  Allocate a pseudo-TTY. (tty - return user's terminal name)
--user        -u                  Username or UID (format: <name|uid>[:<group|gid>])
--workdir     -w                  API 1.35+: Working directory inside the container
```

- **How to extend an existing Docker image?**  
.. Use `Dockerfile` for this. Add `FROM <image-name>` (e.g. `FROM php:5.6-apache`) to specify which image you are about to extend. Any other line in the `Dockerfile` will add a new layer on top of the existing `FROM` image.  
.. `docker-compose.yml` may also be used "to extend" the existing Docker image.  
Read more:  
https://docs.docker.com/engine/reference/builder/#from  
https://docs.docker.com/compose/compose-file/  

- **How to build a custom Docker image?**  
Use `docker build` command relating to `Dockerfile`, for example: `docker build -t phpinfo .`  
Or Docker Compose command `docker-compose up` with the option `--build`, for example: `docker-compose up -d --build`  
Read more:  
https://docs.docker.com/engine/reference/commandline/build/  
https://docs.docker.com/compose/reference/up/  

- **How to run Docker images?**  
Use Docker for that, for example: `docker run -p 8080:80 -d --name=my-phpinfo phpinfo`  
Or Docker Compose, for example: `docker-compose up -d --build`  
If images are already built into containers, the following will also work: `docker start [OPTIONS] CONTAINER [CONTAINER...]`, for example: `docker start my-phpinfo`  
Read more:  
https://docs.docker.com/engine/reference/run/  
https://docs.docker.com/compose/reference/up/  
https://docs.docker.com/engine/reference/commandline/start/  

- **How to use Docker Compose to automate running containers?**  
Use `docker-compose` tool together with the `docker-compose.yml` file in order to reach the automation. Write the `docker-compose.yml` file so others will be able to build, start and configure command easily by running `docker-compose` command later.  
Read more:  
https://docs.docker.com/compose/reference/  
https://docs.docker.com/compose/compose-file/  
https://docs.docker.com/compose/  

- **How to execute a bash shell in a running container?**  
Use `docker exec`, for example: `docker exec -it c9a517f6f751 bash`  
Read more:  
https://docs.docker.com/engine/reference/commandline/exec/  

- **How to copy files into container?**  
Use `COPY` inside of `Dockerfile` to tell which file (or directory) in local machine needs to be copyied to which directory in the container of which the `Dockerfile` is.  
Read more:  
https://docs.docker.com/engine/reference/builder/#copy  

- **Do we need to run `docker build` each time we update the content specified in volumes of `docker-compose.yml` file?**  
No. Volumes allow us to avoid running `docker build` (which copies the files into the container) every time we make a file changes, for example source code change while developing.  
Read more:  
https://docs.docker.com/storage/volumes/  

- **What the `image` key mean in a `docker-compose.yml` file, for example: `image: mariadb:10.1.21`?**  
The `mariadb` service introduces the `image` key, which points to version `10.1.21` of the MariaDB Docker Hub image (https://hub.docker.com/_/mariadb/). The `image` format is just like the `Dockerfile` format: `<name>:<tag>` (some other formats exists too). If you provide `image: mariadb` with no tag, Docker Compose will use the "latest" tag.  
Providing a tag version is a good practice to avoid unexpected changes to the application's environment without explicit control. Using latest should be used with caution on a real project.  
Read more:  
https://docs.docker.com/compose/compose-file/#image  
https://docs.docker.com/engine/reference/builder/#from  

- **What the `expose` key mean in a `docker-compose.yml` file?**  
Expose ports without publishing them to the host machine - they’ll only be accessible to linked services. Only the internal port can be specified.  
For example:
```
expose:
 - "3000"
 - "8000"
``` 
Read more:  
https://docs.docker.com/compose/compose-file/#expose  
 
- **What the `ports` key mean in a `docker-compose.yml` file?**  
Expose ports.  
Read more:  
https://docs.docker.com/compose/compose-file/#ports  
https://docs.docker.com/compose/compose-file/#long-syntax-1  
```
services:
   <service_name>:
       ports:
           - "<local_port>:<container_port>"
```

- **What the `EXPOSE` key mean in a `Dockerfile`?**  
Usage: `EXPOSE <port> [<port>/<protocol>...]`  
The `EXPOSE` instruction informs Docker that the container listens on the specified network ports at runtime. You can specify whether the port listens on TCP or UDP, and the default is TCP if the protocol is not specified.  
*The `EXPOSE` instruction does not actually publish the port.* It functions as a type of documentation between the person who builds the image and the person who runs the container, about which ports are intended to be published. To actually publish the port when running the container, use the `-p` flag on docker run to publish and map one or more ports, or the `-P` flag to publish all exposed ports and map them to high-order ports.  
By default, `EXPOSE` assumes TCP. You can also specify UDP.  
To expose on both TCP and UDP, include two lines.  
To set up port redirection on the host system, see using the `-P` flag. The `docker network` command supports creating networks for communication among containers without the need to expose or publish specific ports, because the containers connected to the network can communicate with each other over any port.  
Read more:  
https://docs.docker.com/engine/reference/builder/#expose  


- **What the `environment` key mean in a `docker-compose.yml` file?**  
The `environment` key defines environment variables for the container.  
Read more:  
https://docs.docker.com/compose/environment-variables/  


- **Where environment variable values could be taken from in case we want to pass it to the container via `docker-compose.yml`?**  
Read more:  
https://docs.docker.com/compose/environment-variables/  
It’s possible to use environment variables in your shell to populate values inside a Compose file:  
```
web:
  image: "webapp:${TAG}"
```
You can set environment variables in a service’s containers with the `environment` key, just like with `docker run -e VARIABLE=VALUE ...`:
```
web:
  environment:
    - DEBUG=1
```
You can pass environment variables from your shell straight through to a service’s containers with the `environment` key by not giving them a value, just like with `docker run -e VARIABLE ...`, the value of the `DEBUG` variable in the container is taken from the value for the same variable in the shell in which Compose is run:  
```
web:
  environment:
    - DEBUG
```
You can pass multiple environment variables from an external file through to a service’s containers with the `env_file` option, just like with `docker run --env-file=FILE ...`:  
```
web:
  env_file:
    - web-variables.env
```
Just like with `docker run -e`, you can set environment variables on a one-off container with `docker-compose run -e`:  
```
docker-compose run -e DEBUG=1 web python console.py
```
You can also pass a variable through from the shell by not giving it a value:  
```
docker-compose run -e DEBUG web python console.py
```
You can set default values for any environment variables referenced in the Compose file, or used to configure Compose, in an environment file named `.env`:
```
$ cat .env
TAG=v1.5

$ cat docker-compose.yml
version: '3'
services:
  web:
    image: "webapp:${TAG}"

```

- **Explain `docker-compose config`**  
Validates and shows the Compose file.  
More info:  
https://docs.docker.com/compose/reference/config/  
```
Usage: config [options]

Options:
    --resolve-image-digests  Pin image tags to digests.
    -q, --quiet              Only validate the configuration, don't print
                             anything.
    --services               Print the service names, one per line.
    --volumes                Print the volume names, one per line.
```

- **When you set the same environment variable in multiple files, what is the priority used by Compose to choose which value to use (Compose file, Environment file, or Dockerfile)?**  
    1. Compose file,
    2. Environment file,
    3. Dockerfile,
    4. Variable is not defined.  
Read more:  
https://docs.docker.com/compose/environment-variables/#configure-compose-using-environment-variables  

- **Is it correct that values of environment variables in the shell take precedence over those specified in the .env file?**  
It's correct.  
Read more:  
https://docs.docker.com/compose/environment-variables/#configure-compose-using-environment-variables  

- **What the `links` key mean in a `docker-compose.yml` file?**  
The `links` format specifies the name and a link alias (`<service>:<alias>`), which enables you to use the alias to communicate with the container.  
While links are not required for containers to communicate — they can reach each other using the service name — it's important to understand that defining the `link` as `- mariadb` is shorthand for `- mariadb:mariadb`. If you want to define an alias for the
service, use the links key with something like `- mariadb:db`, and then you would use `db` as the hostname to communicate with `mariadb` from the app container.  
Read more:  
https://docs.docker.com/compose/compose-file/#links

- **What are the alternatives for using `links` key mean in a `docker-compose.yml` file?**  
Use user-defined networks to facilitate communication between two containers instead of using `--link`. One feature that user-defined networks do not support that you can do with `--link` is sharing environmental variables between containers.  
Read more:  
https://docs.docker.com/compose/compose-file/#links  
https://docs.docker.com/network/  


- **What is the alternative for sharing environmental variables between containers by using `links` key in a `docker-compose.yml`?**  
You can use other mechanisms such as `volumes` to share environment variables between containers in a more controlled way.  
Read more:  
https://docs.docker.com/compose/compose-file/#links  
https://docs.docker.com/network/  


- **There are three types of volumes: host, anonymous, and named. Where do they differ?**  
There are three types of volumes: host, anonymous, and named:  
1.  A host volume lives on the Docker host's filesystem and can be accessed from within the container. To create a host volume:
```
   docker run -v /path/on/host:/path/in/container ...
```  
2. An anonymous volume is useful for when you would rather have Docker handle where the files are stored. It can be difficult, however, to refer to the same volume over time when it is an anonymous volumes. To create an anonymous volume:
```
   docker run -v /path/in/container ...
```  
3. A named volume is similar to an anonymous volume. Docker manages where on disk the volume is created, but you give it a volume name. To create a named volume:
```
   docker volume create somevolumename
   docker run -v name:/path/in/container ...
```  
Read more:  
https://success.docker.com/article/different-types-of-volumes  
https://docs.docker.com/storage/volumes/  
  

- **Explain `docker-compose rm -v`**  
By default, anonymous volumes attached to containers are not removed. We can override this with `-v`.  

- **Explain `docker-compose --file=docker-compose.prod.yml build` followed by `docker-compose --file=docker-compose.prod.yml up -d`**  
This will build and up the container based on the `docker-compose.prod.yml` settings of Docker Compose. By default, Docker Compose looks for a `docker-compose.yml` file, but by using the `docker-compose --file`, you can use an alternate Docker Compose file.  
Read more:  
https://docs.docker.com/compose/reference/overview/#command-options-overview-and-help  
https://docs.docker.com/compose/reference/build/  
https://docs.docker.com/compose/reference/up/  

- **What happens when a host machine (your development machine) mounts a host directory (volume) on an existing path in the container (e.g. `/srv/app`)?**  
It overrides the existing files in that path. The mount overlays but does not remove the pre-existing content. Once the mount is removed, the content is accessible again.  
Read more:  
https://docs.docker.com/storage/volumes/  

- **Explain: `docker build -t ch05-composer .`**   
This builds docker image with the tag `ch05-composer` from the `Dockerfile` in a current directory (`.`).  
Read more:  
https://docs.docker.com/engine/reference/commandline/build/  

- **Explain: `docker run --rm ch05-composer /usr/local/bin/composer --version`**  
This runs a command `/usr/local/bin/composer --version` inside of the container tagged as `ch05-composer`. The `--rm` flag automatically removes the container on exit, which means it does not show up when you run `docker ps -a`.  
Read more:  
https://docs.docker.com/engine/reference/commandline/run/  

- **What is the difference between `ADD` and `COPY` inside a `Dockerfile`?**  
The major difference is that `ADD` can do more than `COPY`. `ADD` allows `<src>` to be an URL. If the `<src>` parameter of `ADD` is an archive in a recognised compression format, it will be unpacked.  
The Best practices for writing `Dockerfile`s suggests using `COPY` where the magic of `ADD` is not required. Otherwise you are likely to get surprised someday when you mean to copy `keep_this_archive_intact.tar.gz` into your container, but instead you spray the contents onto your filesystem.  
Read more:  
https://docs.docker.com/engine/reference/builder/#add  
https://docs.docker.com/engine/reference/builder/#copy  
https://stackoverflow.com/questions/24958140/what-is-the-difference-between-the-copy-and-add-commands-in-a-dockerfile  
https://docs.docker.com/develop/develop-images/dockerfile_best-practices/  

- **What is the `WORKDIR /var/www/html` for in case this line is in a `Dockerfile`?**  
The `WORKDIR` instruction sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY` and `ADD` instructions that follow it in the `Dockerfile`. If the `WORKDIR` doesn’t exist, it will be created even if it’s not used in any subsequent `Dockerfile` instruction.  
The `WORKDIR` instruction can be used multiple times in a `Dockerfile`. If a relative path is provided, it will be relative to the path of the previous `WORKDIR` instruction.  
Read more:  
https://docs.docker.com/engine/reference/builder/#workdir  

- **What is `.dockerignore`? For example, `echo "app/vendor/" >> .dockerignore`?**  
The `.dockerignore` file resides in the same directory as the `Dockerfile` file and works similarly to a `.gitignore` file in `git`, ensuring that unintended files are left out during a `COPY` or `ADD` instruction.  
Read more:  
https://docs.docker.com/engine/reference/builder/#dockerignore-file  
https://codefresh.io/docker-tutorial/not-ignore-dockerignore/  

- **What are the ways of installing private Composer packages in Docker?** (relates to Composer - PHP dependency manager)  
1. Copy an SSH key into the Docker image from a build machine  
2. Install Composer dependencies on a credentialed machine and then copy the `vendor/` folder into the image during a build  
3. Use an OAuth token with a Composer config file during a `docker build`  

The example for the 3rd option:
1. Create a private git project on Bitbucket.org
2. Create a read-only OAuth consumer on Bitbucket.org ( https://getcomposer.org/doc/06-config.md#bitbucket-oauth , https://confluence.atlassian.com/bitbucket/oauth-on-bitbucket-cloud-238027431.html , https://getcomposer.org/doc/05-repositories.md#bitbucket-driver-configuration )
3. Generate a unversioned `auth.json` config in our project ( `chmod u+x auth-setup.sh`, `export BITBUCKET_CONSUMER_KEY=my-key`, `export BITBUCKET_CONSUMER_SECRET=my-secret`, `./auth-setup.sh`, `echo "auth.json" >> app/.gitignore` )
4. Define the private Composer dependency as a required package
5. Run our existing docker build command (e.g. `docker build --no-cache -t ch05-composer .` )

- **Explain: `docker build --no-cache`**  
Do not use cache when building the image (including do not cache the outcome of each layer of `Dockerfile`).  
Usage: `docker build [OPTIONS] PATH | URL | -`  
Read more:  
https://docs.docker.com/engine/reference/commandline/build/  

- **Explain: `docker run --name nginx-container -p 8080:80 -d nginx:1.12`**  
Run Docker container FROM `nginx:1.12` image ( https://hub.docker.com/_/nginx/ ).  
`--name nginx-container` - assign the name `nginx-container` to the container.  
`-p 8080:80` - map a container᾿s port `80` to host's port `8080`.  
`-d` - to start a container in detached mode (in a foreground).  
Read more:  
https://docs.docker.com/engine/reference/run/  
https://hub.docker.com/_/nginx/  

- **Explain: `docker stop $(docker ps -q)`**  
Stops all running containers.  
`-q` stands for `--quite` and is for "Only display numeric IDs"  
Read more:  
https://docs.docker.com/engine/reference/commandline/stop/  
https://docs.docker.com/engine/reference/commandline/ps/  

- **Explain: `docker rm $(docker ps -aq)`**  
Remove all containers.
`-q` stands for `--quite` and is for "Only display numeric IDs"  
`-a` stands for `--all` and is for "Show all containers, including stopped ones (default, without `-a`, shows just running)"  
Read more:  
https://docs.docker.com/engine/reference/commandline/rm/  
https://docs.docker.com/engine/reference/commandline/ps/  

- **Explain: `docker cp nginx-container:/etc/nginx/nginx.conf .docker/nginx/nginx.conf`**  
Copy files/folders between a container and the local filesystem.  
In this case, file `/etc/nginx/nginx.conf` from the container named `nginx-container` will be copied to `.docker/nginx/nginx.conf` in a local filesystem.  
Read more:  
https://docs.docker.com/engine/reference/commandline/cp/  
Usage:  
```
docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-
docker cp [OPTIONS] SRC_PATH|- CONTAINER:DEST_PATH
```

- **Explain the following found in `docker-compose.yml`:**  
```
version: "3"
services:
  nginx:
    build:
      context: .
      dockerfile: .docker/nginx/Dockerfile
```
`version: "3"` - version 3 of the Compose file format.  
`services:` - lists services (containers) available.  
`nginx:` - the name given to the service (container).  
`build:` - configuration options that are applied at build time.  
`context: .`  
Either a path to a directory containing a Dockerfile, or a url to a git repository.  
When the value supplied is a relative path, it is interpreted as relative to the location of the Compose file. This directory is also the build context that is sent to the Docker daemon.  
Compose builds and tags it with a generated name, and use that image thereafter.  
`dockerfile: .docker/nginx/Dockerfile`  
Alternate Dockerfile. Compose uses an alternate file to build with. A build path must also be specified.  
In the example, the `context` and `dockerfile` keys are equivalent to `docker build -f .doker/php/Dockerfile -t <the-tag> .`, the last dot being the current folder (`context`).  
Read more:  
https://docs.docker.com/compose/compose-file/  


- **Explain the following found in `docker-compose.yml`:**  
```
version: "3"
networks:
  app-tier:
    driver: bridge
services:
  app:
    networks:
      - app-tier
  nginx:
    networks:
      - app-tier
```
`version: "3"` - version 3 of the Compose file format.  
`services:` - lists services (containers) available.  
`app:`, `nginx:` - the names given to the services (containers).  
`networks` keys under services - networks to join, referencing entries under the top-level `networks` key.  
Read more:  
https://docs.docker.com/compose/compose-file/  
https://docs.docker.com/compose/compose-file/#networks  
https://docs.docker.com/compose/networking/  
https://github.com/docker/labs/blob/master/networking/README.md  
https://github.com/docker/labs/blob/master/README.md  

- **Explain: `CMD ["/usr/bin/caddy", "--conf", "/etc/Caddyfile", "--log", "stdout"]` forund in `Dockerfile`**  
The CMD instruction has three forms:  
```
    CMD ["executable","param1","param2"] (exec form, this is the preferred form)
    CMD ["param1","param2"] (as default parameters to ENTRYPOINT)
    CMD command param1 param2 (shell form)
```
There can only be one `CMD` instruction in a `Dockerfile`. If you list more than one `CMD` then only the last `CMD` will take effect.  
The example given is `CMD` with `/usr/bin/caddy` as executable and the rest (`--conf`, `/etc/Caddyfile`, `--log`, `stdout`) as parameters.  
`--conf` - The `Caddyfile` to use to configure Caddy. Must be a valid path to the file, either relative or absolute. Can be a glob string as well, to load all matching files as if they were imported into a single configuration. In the case of the example, the file is `/etc/Caddyfile`.  
`--log` - Enable the process log. The value must be either the path to a log file, `stdout`, or `stderr`. Caddy will create the log file if it does not already exist. This file will be used to log information and errors that occur during runtime. The log file is rotated when it gets large, so it is safe to use for long-running processes. In the case of example, log is set to be `stdout`.  
Read more:  
https://docs.docker.com/engine/reference/builder/#cmd  
https://caddyserver.com/docs/cli  
https://stackoverflow.com/questions/3385201/confused-about-stdin-stdout-and-stderr  

- **What are ways to use old PHP version (older than supported by https://hub.docker.com/_/php/) with Docker?**  
 1. we can use a PHP package from an older Linux version
 2. we can build PHP (and the required modules) from source

- **What is the meaning of `entrypoint` in `docker-compose.yml` file**?  
For example:
```
version: "3"
services:
  app:
    image: cakephp-app
    container_name: cakephp-app
    build:
      context: .
      dockerfile: .docker/Dockerfile
    ports:
      - 8888:80
    volumes:
      - .:/srv/cakephp
  cake:
    image: cakephp-app
    container_name: cakephp-console
    volumes:
      - .:/srv/cakephp
    entrypoint: [
      "/srv/cakephp/app/Console/cake",
      "-app", "/srv/cakephp/app"
    ]
```
Override the default entrypoint. Setting entrypoint both overrides any default entrypoint set on the service’s image with the ENTRYPOINT `Dockerfile` instruction, and clears out any default command on the image - meaning that if there’s a `CMD` instruction in the `Dockerfile`, it is ignored.
Read more:  
https://docs.docker.com/compose/compose-file/#entrypoint  

- **Can `entrypoint` and `CMD` be used together in the same `Dockerfile` or in the `docker-compose.yml` service block "extending" the same `Dockerfile`?**  
Setting `entrypoint` both overrides any default `entrypoint` set on the service’s image with the `ENTRYPOINT` `Dockerfile` instruction, and clears out any default command on the image - meaning that if there’s a `CMD` instruction in the `Dockerfile`, it is ignored.  
The main purpose of a `CMD` is to provide defaults for an executing container. These defaults can include an executable, or they can omit the executable, in which case you must specify an `ENTRYPOINT` instruction as well.  
Given how much easier it is to override the `CMD`, the recommendation is use `CMD` in your `Dockerfile` when you want the user of your image to have the flexibility to run whichever executable they choose when starting the container. For example, maybe you have a general Ruby image that will start-up an interactive irb session by default (`CMD irb`) but you also want to give the user the option to run an arbitrary Ruby script (`docker run ruby ruby -e 'puts "Hello"'`).  
In contrast, `ENTRYPOINT` should be used in scenarios where you want the container to behave exclusively as if it were the executable it's wrapping. That is, when you don't want or expect the user to override the executable you've specified.  
Most of the time you can achieve the same thing with `CMD` as with `ENTRYPOINT`, but the use of `ENTRYPOINT` sends a strong message that this container is only intended to run this one command.  
Both the `ENTRYPOINT` and `CMD` instructions support two different forms: the shell form and the exec form.  
When using the shell form, the specified binary is executed with an invocation of the shell using `/bin/sh -c`. You can see this clearly if you run a container and then look at the docker ps output.  
When the `exec` form of the `CMD` instruction is used the command will be executed without a shell. For example: `CMD ["/bin/ping","localhost"]`. In the example case, `/bin/ping` is being run directly without the intervening shell process (and, as a result, will end up as PID 1 inside the container). Whether you're using `ENTRYPOINT` or `CMD` (or both) the recommendation is to always use the `exec` form so that's it's obvious which command is running as PID 1 inside your container.  
Combining `ENTRYPOINT` and `CMD` allows you to specify the default executable for your image while also providing default arguments to that executable which may be overridden by the user. For example, `ENTRYPOINT ["/bin/ping","-c","3"]` and the later `CMD ["localhost"]` in one file.  
When using `ENTRYPOINT` and `CMD` together it's important that you always use the exec form of both instructions. Trying to use the shell form, or mixing-and-matching the shell and exec forms will almost never give you the result you want.  
For example:
```
Dockerfile    Command
ENTRYPOINT /bin/ping -c 3
CMD localhost    
/bin/sh -c '/bin/ping -c 3' /bin/sh -c localhost

ENTRYPOINT ["/bin/ping","-c","3"]
CMD localhost    
/bin/ping -c 3 /bin/sh -c localhost

ENTRYPOINT /bin/ping -c 3
CMD ["localhost"]"    
/bin/sh -c '/bin/ping -c 3' localhost

ENTRYPOINT ["/bin/ping","-c","3"]
CMD ["localhost"]    
/bin/ping -c 3 localhost
```
The only one of these that results in a valid command string is when the `ENTRYPOINT` and `CMD` are both specified using the exec form.  
If you want your image to actually do anything when it is run, you should definitely configure some sort of `ENTRYPOINT` or `CMD` in you `Dockerfile`. However, remember that they aren't mutually exclusive. In many cases you can improve the user experience of your image by using them in combination.  
Read more:  
https://www.ctl.io/developers/blog/post/dockerfile-entrypoint-vs-cmd/  
https://docs.docker.com/engine/reference/builder/#cmd  
https://docs.docker.com/engine/reference/builder/#entrypoint  

- **What is Docker registry?**  
At a basic level, a Docker registry is a storage and content delivery system, holding named Docker images, available in different tagged versions.  
There are many Docker repositories our there dealing with Docker registry, such as Quay, Google Container, Registry, Amazon EC2 Container Registry, and GitLab, to name a few. The default one for the Docker is the Official Docker Hub (docker.io).  
Image names as used in typical docker commands reflect their origin:  
- `docker pull ubuntu` instructs docker to pull an image named `ubuntu` from the official Docker Hub. This is simply a shortcut for the longer `docker pull docker.io/library/ubuntu command`
- `docker pull myregistrydomain:port/foo/bar` instructs docker to contact the registry located at `myregistrydomain:port` to find the image `foo/bar`  
Read more:  
https://docs.docker.com/registry/introduction/  

- **Explain `sudo docker run -d --restart=unless-stopped -p 8080:8080 rancher/server`**  
**`sudo`** - allows a permitted user to execute a command as the superuser.  
**`docker`** - Docker software in action.  
**`run`** - Docker runs processes in isolated containers. A container is a process which runs on a host. The host may be local or remote. When an operator executes `docker run`, the container process that runs is isolated in that it has its own file system, its own networking, and its own isolated process tree separate from the host.  
**`-d`** - Start a container in detached mode (in a background).  
**`--restart=`** - Using the `--restart` flag on Docker run you can specify a restart policy for how a container should or should not be restarted on exit. When a restart policy is active on a container, it will be shown as either `Up` or `Restarting` in `docker ps`.  
**`unless-stopped`** - Always restart the container regardless of the exit status, including on daemon startup, except if the container was put into a stopped state before the Docker daemon was stopped.  
In short, `--restart=unless-stopped` is a restart policy that restarts the container unless we manually stop it. Even if we reboot our droplet (e.g. on DigitalOcean), the container will restart afterward.  
**`-p 8080:8080`** - Publish a container᾿s port `8080` to the host. The exposed port is accessible on the host and the ports are available to any client that can reach the host. Format: `hostPort:containerPort`  
**`rancher/server`** - Docker images are the basis of containers. An Image is an ordered collection of root filesystem changes and the corresponding execution parameters for use within a container runtime. An image typically contains a union of layered filesystems stacked on top of each other. An image does not have state and it never changes. In this case, the image used is `rancher/server` found in the default Docker containers registry (docker.io). 
Read more:  
https://man.cx/sudo  
https://docs.docker.com/engine/reference/commandline/cli/  
https://docs.docker.com/engine/reference/run/  
https://docs.docker.com/engine/reference/run/#detached--d  
https://docs.docker.com/engine/reference/run/#restart-policies---restart  
https://docs.docker.com/engine/reference/run/#expose-incoming-ports  
https://docs.docker.com/glossary/?term=image  
https://hub.docker.com/r/rancher/server/  
https://www.digitalocean.com/products/droplets/  

- **Explain `docker build -f docker/Dockerfile -t registry.gitlab.com/sugalvojau/projectname:$tag .`**  



Read more:  
- https://github.com/moby/moby/issues/13490  
- Docker (https://docs.docker.com/)  
- Docker labs and tutorials (https://github.com/docker/labs)  
- Docker Up and Running (http://shop.oreilly.com/product/0636920036142.do) is a book by Karl Matthias and Sean Kane  
- Docker screencasts online (https://serversforhackers.com/t/containers)  
- Shipping Docker (https://serversforhackers.com/shipping-docker)  





