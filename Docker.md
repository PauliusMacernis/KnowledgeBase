 ## Docker
 
- **What is each of the following commands for: `docker`, `docker-compose`, `docker-machine`?**  

- **What is the difference between using `docker run` and Docker compose?**  

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

- 

- 
