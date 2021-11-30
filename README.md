# Docker Commands

__Docker Version :__  

```
docker version
```  
    
__Information of Docker container and images in your docker :__  

```
docker info
```  
    
__Pulls images from [Docker Hub](https://hub.docker.com/_/nginx) :__   

```
docker pull nginx:1.21.4-alpine
```


__For listing all images in your docker :__  

```
docker image ls
```

or

```
docker images
```

__For removing Image from Docker :__

```
docker image rmi nginx:1.21.4-alpine
```

    
__For deploying application image in your docker :__  

docker run --publish {image_file_expose_port:local_machine_port} --name {container_name} {image_name:version}

```
docker run -p 8080:80 --name nginx nginx:1.21.4-alpine
```

docker run --detach --publish {image_file_expose_port:local_machine_port} --name {container_name} {image_name:version}

```
docker run -d -p 8081:80 --name nginx2 nginx:1.21.4-alpine
``` 

__For listing all container with up status in your docker :__  

```
docker container ps
```

__For listing all container in your docker :__  

```
docker container ps -a
```

__For executing bash command inside your docker container :__  

docker exec -it {container_name} sh  

```
docker exec -it nginx sh
```


__For stoping container in your docker :__  

docker stop {container_name}

```
docker stop nginx 
``` 


__For starting container in your docker :__ 

docker start {container_name}

```
docker start nginx 
``` 

__For removing container in your docker :__  

docker rm {container_name}

docker rm -f {container_name} #for force remove container while it is still in process/running  

```
docker rm nginx

#for force remove container while it is still in process/running  

docker rm -f nginx 
``` 
    

__Creating image file for your application :__  

Following code is for creating image file for html which will be deploy in docker nginx container.  
Create a file with name Dockerfile in root directory of your application without any extension and add following lines in it.  

``` 
# We are extending everything from nginx image ...

FROM nginx:1.21.4-alpine

# COPY {path-to-your-application} {path-to-webapps-in-docker-nginx}  

COPY $PWD/src /usr/share/nginx/html
``` 

```
#docker image build -t {your_name/image_name} .  
docker image build -t prueba2021:v1 .  
```

Now if you list images in your docker `docker images` it will contain image that you have just created for your application.  


