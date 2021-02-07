# docker-learning
learning docker
## build initial docker file
[01-Dockerfile](./01-Dockerfile)
## Commands
- docker history
- docker inspect
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

  

  
