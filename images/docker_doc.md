# Docker

Show all containers
```
docker ps -a          
```
Remove things
```
docker rm <name> 
```

Run container in interactive mode
```
docker exect -it <containerID/name>
```
Run docker container in detached or interactive mode naming the container and running a specific main command

docker run [-d,-- name,-it] ubuntu:latest [command]
- example:
```
docker run -d --name ubuntu_image ubuntu:latest tail -f /dev/null
```

```
docker run -d -p 8080:80 --name proxy nginx:latest 
```
-p (publish) expose localmachine ports to container port [Local_machine_ports:container_port] [8080:80]

 docker logs -f <container>

-f (follow)

Docker bindmounts 

(Check backslashes for windows correct path form)

```
docker run -d --name db -v //wsl.localhost/Ubuntu-20.04/home/tarkangel/gitRepos/docker/bind_mounts:/data/db mongo
```
Docker Volumes
Creates volume space to store container data
```
docker volume create dbdata             
```
Creates container with a Volume mounted in data/db directory 
```
docker run -d --name db --mount src=dbdata,dst=/data/db mongo 
```

Copy a file from your local machine to a docker container
```
docker cp test.txt ubuntu:/test_dir/          
docker cp <file> <container>:</dest/path/inContainer>
```
Copy file from container to your localmachine/current working directory
```
docker cp ubuntu:/test_dir/test.txt test.txt
```

```
docker cp <container>:</path/inContainer/  <new/same name for the file/directory>
```
To login to docker

```
docker login -u <your_username>   
#Pass request will be prompted
```
To push an image to your DockerHub Repo
```
docker tag <image>:<tag> <your_username>/<image>:<tag>
```
```
docker push <your_username>/<image>:<tag>
```
