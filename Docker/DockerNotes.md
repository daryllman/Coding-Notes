# Docker Notes

Simple notes to record commonly used commands



**Pull Images from Docker Remote**

```
docker pull <image name>
```



**Docker Run**

```
docker run -it -d <image name>
docker run -p 5000:80 -it -d <image name>
docker run -it -d --name ImageName <image name> #with image name for ease of ref
```



**List running docker containers**

```
docker ps
docker ps -a #shows all running and exited containers
```



**Access running docker container**

```
docker exec -it <container id/name> bash
```



**Docker copy files**

```
docker cp foo.txt mycontainer:/foo.txt
```





**Docker stop**

```
docker stop <container id>
docker kill <container id> #stop its execution immediately if its taking too long
```



**Docker commit** 

```
docker commit <conatainer id> <username/imagename>
```

creates a new image of an edited container on the local system



**Docker login**

```
docker login
```





**Docker push**

```
docker push <username/image name>
```

This command is used to push an image to the docker hub repository



**List available docker images locally**

```
Docker images
```



**Remove docker container/image**

```
docker rm <container id> #delete a stopped container
docker rmi <image-id> #delete an image from local storage

```



**Docker build**

```
docker build <path to docker file>
docker build . #from docker file
docker build . #from docker file, with tag name bulletinboard:1.0
docker build --tag bulletinboard:1.0 . #from docker file, with tag name
docker build . #from docker file
```



**Save image as file**

```
docker save -o filename.tar <image name>
```



**Check available images**

```
docker image ls
docker images
```



**Load docker from file**

```
docker load --input filename.tar
```



**Inspect running containers**

```
docker inspect <name> | grep Address
```

