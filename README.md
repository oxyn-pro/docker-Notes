# docker_instruction
## The small instruction created by my own notes about docker.  Commands, Templates

## Commands to work with docker images, containers
- ### Create container, create directories/files inside a container:
```
docker run --name ubuntu_bash --rm -i -t ubuntu bash
```
This will create a container named ubuntu_bash and start a Bash session.

```
docker exec -t <container_id> bash
```
Execute an interactive bash shell on the container:

- ### Check container's id, stop container, start container, remove a container:
```
docker ps -aqf "name=containername"
```
Shows container's id

```
docker start <container_id>"
```
Starts stopped container

```
docker ps -a 
```
Lists containers (and tells you which images they are spun from)

```
docker stop <container_id> 
```
Stops a container

```
docker rm <container_id>  
```  
Removes a stopped container

```
docker rm -f <container_id> 
```
Forces the removal of a running container (uses SIGKILL)

```
docker rm -f <container_id>
```
Delete all containers that are not running.

- ### List images, Remove images

```
docker images    
```           
Lists images 

```
docker rmi <image_id>       
```
Removes an image. Will fail if there is a running instance of that image i.e. container

- ### Deleting running containers, deleting stopped containers
```
docker container rm $(docker ps -a -q)
```
Kill all running containers.

```
docker container kill $(docker ps -q)
```
Kill all stopped containers, all networks not used by at least one container, all dangling images. all build cache

- ### FORSE DELETE IMAGES
```
docker system prune
```
Forces removal of image even if it is referenced in multiple repositories, i.e. same image id given multiple names/tags.
Will still fail if there is a docker container referencing image

## How do ports work?

![How does ports work in Docker](https://user-images.githubusercontent.com/69118015/129787006-3344b20a-12f4-44f1-93d1-711140e5f847.png)

### Mapping different ports to the container's port
```
docker run -p 8080:80 -p 5000:80 -d <image_name>
```
It will create a container and maps differenct localhost ports to the main container's port

## Problems with "File Sharing"
```
Cannot create container for service db: status code not OK but 500: {"Message":"Unhandled exception: Filesharing has been cancelled","StackTrace":" at Docker.ApiServices.Mounting.FileSharing.d__6.MoveNext()
```

**(For Docker Desktop (windows)) The solution is to share the project path folder drive in Docker for starter. If that doesn't work, restart docker.**

![image](https://user-images.githubusercontent.com/69118015/127782715-f599be1b-dffc-411c-9893-5111429190ce.png)


## Deployment different apps through Docker to cloud services like: AWS, Google Cloud, Azure

Found an amazing video from "FreeCodeCamp" about this topic: https://www.youtube.com/watch?v=-ANCcFQBk6I&ab_channel=freeCodeCamp.org
