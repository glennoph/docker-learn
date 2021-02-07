# docker-learning
learning docker
## build initial docker file
[01-Dockerfile](./01-Dockerfile)
## Commands
- `docker history`
- `docker inspect`
## Good Practices
- RUN commands create separate layer... 

```
RUN apt-get update \
	&& apt-get -y upgrade
```
- COPY srcfile target
- ADD http://source-file target
- ADD compressed.tar.gz extracted-target
- ENV env_var_name env_value
  - env reference ${env_var_name}
- ARG var_name_1 # var value is passed via docker build : 

`docker build --build-arg var_name_1=value1 .`

- ARG var_name_2=value2 # default value is value2
  
`ENV var_name_2=${var_name_2}` # env var uses the arg 

- NB ARG and ENV values are displayed in clear text, no pw
## Docker Images
- `docker images` # list of images
- `docker images -q` # list of images quiet (only sha)
- `docker ps -q` # list of containers quiet (only sha)
### remove all images
- `docker rmi $(docker images -a -q)` # remove all images
### remove all containers
- `docker rm $(docker ps -a -q)` # remove all images
### tag an image during build
- `docker build -t TAGREPO/INAME:v1.0 .` # tag is v1.0, image name is INAME, tag repo is TAGREPO (opt)
### login to registry
- `docker login`
- `docker logout`
- `docker login -u uuu -p ppp https://mydockerregistry.com` # log in to a private registry
### retag image for registry
- `docker tag oldimage:oldversion newregistry/newimage:newtag`
- `docker push newregistry/newimage:newtag`
### pull image from docker hub
- `docker pull REG/IMAGE:tag`
## Container
### Command
- `docker run [OPTIONS] IMAGE [COMMAND] [args]`
- `docker ps -a` # list all containers
#### docker run options

| Options | Meaning                       |
|---------|-------------------------------|
| -i      | interactive, keeps stdin open |
| -d      | detached, run in background   |
| -t      | pseudo-tty shell              |
| -it     | launched in shell             |
| -id     | interactive & detached        |
|         |                               |

### Clean up 
- `docker rm -f $(docker ps -aq)` # clean up all containers with force
- `docker rmi $(docker images -q)` # clean up all images
### Pull and Run, 1 command
- `docker run -it IMAGE COMMAND` # pull and run image in a shell
### Name a container
- `docker rename OLD NEW` # where OLD is from ps -a/NAMES
- `docker stop ` # stop container
- `docker start C1 [C2] ` # start container
- `docker restart C` # restart container
- `docker restart -t 10  C` # restart container after 10 seconds
- `docker exec -it CONTAINER COMMAND` # execute command in running container in a shell
- `docker exec -it -u USER CONTAINER COMMAND` # execute command in running container in a shell as USER



