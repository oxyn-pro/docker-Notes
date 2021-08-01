# docker_instruction
#### The small instruction created by my own notes about docker.  Commands, Templates

## Commands to work with docker images, containers
> docker ps -a 

Lists containers (and tells you which images they are spun from)

>docker ps -aqf "name=containername"

Shows container's id

>docker images    
           
Lists images 

>docker rm <container_id>  
  
Removes a stopped container

>docker rm -f <container_id> 

Forces the removal of a running container (uses SIGKILL)

>docker rmi <image_id>       

Removes an image. Will fail if there is a running instance of that image i.e. container

> docker rmi -f <image_id>    

Forces removal of image even if it is referenced in multiple repositories, i.e. same image id given multiple names/tags. Will still fail if there is a docker container referencing image

## Problems with "File Sharing"
```
Cannot create container for service db: status code not OK but 500: {"Message":"Unhandled exception: Filesharing has been cancelled","StackTrace":" at Docker.ApiServices.Mounting.FileSharing.d__6.MoveNext()
```

**(For Docker Desktop (windows)) The solution is to share the project path folder drive in Docker for starter. If that doesn't work, restart docker.**

![image](https://user-images.githubusercontent.com/69118015/127782715-f599be1b-dffc-411c-9893-5111429190ce.png)


## Deployment different apps through Docker to cloud services like: AWS, Google Cloud, Azure

Found an amazing video from "FreeCodeCamp" about this topic: https://www.youtube.com/watch?v=-ANCcFQBk6I&ab_channel=freeCodeCamp.org
