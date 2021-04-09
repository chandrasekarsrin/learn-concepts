## Containers
* completely isolated components.
* Some of the already existing containers are: lxc, lxd, etc...
* Docker uses lxc

## Docker
* matrix from hell. lot of combinations a software have to be tested to make sure everything goes well in production.
* build once as a docker image and ship it anywhere.
* shares the kernel. Hence we cannot run windows container on a linux machine. But when you run docker on windows, and run a linux container on it, under the hood docker on windows executes this container on a virtual machine with linux image on it.

containers (application, libs and dependencies)
docker (manages containers)
OS (host os)
hardware infrastructure (host infrastructure)

VM (application, libs, dependencies and OS)
hypervisor
hardware infrastructure

* VM needs more resources and consumes lot of size.
* Container boots up faster than VM.
* docker have less isolation than containers.

* We need both containers and virtual machines in real world. In a enterprise we will have infrasturcture virtualized and containers are run on top of it.
* Most of the products are already dockerized and available in public docker hub. 

* main purpose is to package and containerize. docker is not meant to virtualize and run applications on the same hardware.

## Operating system

* it contains OS Kernel and softwares.
* Kernel is a software that interacts with hardware.

## Container vs Image
* A image is a package, template or plan helps to create one or more containers.
* Containers are running instances of images that are isolated and have own environment and set of processes.

* developer can configure the runtime for his application using a dockerfile and hand over the image to the ops team. 

## Docker community vs Enterprise edition
* Enterprise: certified and supported container platform with features like: image management, image security, universal control plane for managing and orchestrating container.

## Basic Docker commands:

docke ps:
* shows running containers

docker ps -a:
* shows all the containers including stopped or exited.

docker rm:
* to remove the container permanently.
* docker run -it centos bash : gives a bash inside container.

docker stop:
* stops the running container.

docker images:
* list images

docker rmi:
* to remove images permanently from machine.
* make sure you dont have any container referencing to this image before deleting.

docker pull:
* pulling an image in advance

docker exec :
* to run commands inside running container.

docker run:
* starts a container.
* if the image is not running a process inside it then container will exit. container will only live as long as the application/process inside it is running.
### Run - Attach and detach
* by default when we run docker run it will attach to the console for ouput.

docker run -d imagename
: running the docker in detached mode in the background.

docker attach container-id:
*  to attach again to the container.

* By default docker will not read inputs from standard input even if you attach it to the terminal. you should use -i option with docker run.
* still the terminal will not be visible. for this we need to use -t option.
so -it together gives this feature.

How to access applications deployed as docker?
1. dockerhostip(192.168.1.5):port 
2. port is port forwarded using the -p option.  

every docker container that we spin will attach itself to a default network(bridge network) and get an ip address.

Volume mapping:
* dump lot of data in a database. and database stores it in /var/lib/mysql. 
* if the container is deleted then the data is lost.

docker run -v /opt/datadir:/var/lib/mysql mysql

* specify the directory on the dockerhost to dirctory inside the container. in this way docker will mount this directory onto the container. thus will remain even if container exited.

docker inspect container-id:
* returns all the details about the container in json format.
* state, mount, configuration data, network details.
* will also show env variables.

docker logs: 
* to see the container logs(it will fetch from stdout)

### Advanced options for docker run:
docker run ubuntu cat /etc/*release*
* executes the command when run.

docker run ubuntu:17.10 cat /etc/*release*
* to fetch a particular ubuntu tag.

docker run ubuntu sleep 15
* by default docker directly attaches to the terminal.
* and hence terminal swill sleep for 15s.

docker run -d ubuntu sleep 15
* by using detached mode we can detach the stdout of the container from the current terminal.

docker attach container-id:
* this will attach back the contianer to the current terminal.

docker run timer
* prints the current time every second.
* this runs infinitely
docker run -d timer
* to run it in a detached mode.

## Docker images:
How to create your own image?
* either we cannot find an image for a component that we wanted to use.
* or your application that you are building.

steps to install my app manually?
1. os
2. update apt repo
3. install dependencies using apt command
4. install python dependencies using pip command
5. copy the sourcecode to some folder like /opt
6. run the webserver  using flask command.

FROM ubuntu

RUN apt-get update
RUN apt-get  install python

RUN pip install flask
RUN pip install flask-mysql

COPY . /opt/source-coode

ENTRYPOINT FLASK_APP=/opt/sourcecode/app.py flask run



* Dockerfile is a text file written in a specific format which docker can understand. it is in instruction and argument format.
* all docker file should start from FROM baseimage.
* copies file from local system to docker image.
* entry point allows us to specify a command that will be run when the image is run as a container.
* docker builds this as layered architecutre.

docker history:
* will show the build execution log of image built.

* you can container many applications like browser, skype, spotify, etc..

environment variables:
docker run  -e APP_COLOR=blue image

### Command vs entrypoint
docker run ubuntu
* it runs an instances of ubuntu and exits immediately.
* conatiners are meant to run a specific task or process.
* container only lives as long as task or process inside it is running.
* CMD : defines the program to be run
FROM ubuntu
CMD sleep 5 or CMD ["sleep", "5"] 
* you can override the CMD in docker run ubuntu sleep 10
* ENTRYPOINT:  its like command instruction but only specify the program that needs to be run. all the arguments will be taken from docker run.

FROM ubuntu
ENTRYPOINT ["sleep"]

* both entrypoint and cmd can be used to give default arguments. but to this to happen you need to have both entrypoint and cmd in json array format.

FROM ubuntu
ENTRYPOINT ["sleep"]
CMD["5"] // default ARG value.

* docker run --entrypoint sleep2.0 10

## Docker compose: 
* going forward we will use yaml files.
if we want to run more number of services then we can use docker compose.
* create config: docker-compose.yml. 

docker compose up

* simply starts all the containers configured in yaml file.

docker run -d --name=redis redis
docker run -d --name=db postgres
docker run -d --name=vote -p 5000:80 --links redis:redis voting
docker run -d --name=result -p 5001:80 result-app
docker run -d --name=worker worker

--links is an option 
adds an /etc/host entry to resolve redis.
using links is going to be deprecated in futre.
because we have some advanced features now.


creating docker compose file:

redis:
  image: redis
db:
  image: db
vote:
  build: ./voting  # builds and runs the image.
  ports:
    - 5000:80
  links:
    - redis:redis

docker compose up

this is a version 1 of docker compose file.
Limitations:
* it will not change network
* you cannot order the container start.

version: 2
services:


* in version 1 docker compose attaches all the containers to default bridge network. and uses links to communicate.
* in further versions, links is not required.

#####################

## Docker Engine

* docker daemon
* docker REST API
* docker CLI 

CLI: can be in a different host and use remote docker engine. docker -H=ip:port run ngnix

* docker uses namespaces to isolate workspaces(network, processid, inter process communitation, mounts, unix time sharing). 
* all the process running inside containers are essentially running on the host itself by achieveing isolation through namespaces.

cgroups:
* by default there is no limit on amount of system resources(cpu and memory) a container can use.
* container achieves this using cgroups
docker run  --cpus=.5 ubuntu
docker run --memory=100m ubuntu

## Docker storage:
* where and how docker stores data and how it manages in local file system.

/var/lib/docker  : this is where it stores all its data.
aufs
containers
image
volumes

* image created using docker build is immutable.
* when we start the container an temporary container layer (read write )  where it writes logs, etc..\
* when some of the files baked into the image was edited then it is copied to this temporary layer for any writes. this is called copy on write.

* if we would like to preserve the data across container restarts we should use volumes.

Volume mount: mounts volume 
bind mount: mounts any path in the host machine.

-v : old way
--mount: new way. more verbose
--mount type=bind,source=/data/mysql,target=/var/lib/mysql

* Docker uses storage driver to enable layered architecture. These drivers takes care of creating read write layer, copy on write, etc..
Some of the available drivers: AUFS, ZFS, BTRFS, Device Mapper, Overlay, Overlay2. Docker will automatically choose best storage driver based on the host operating system.

## Docker Networking :)

* when you install docker it creates 3 newtorks:

Bridge :
* default network
* private network created by docker.
* usually 172.17.* series.
* to access containes port mapping is required.
* host network also can be used but it directly uses host's port.
None :
* containers are not attached to any network and dont have access to any other container or network.
* they run on isolation.
Host:
* same network as host.

* New internal networks can be created to isolate networks between containers.
* container can reach other using their names. (Embedded DNS helps: always runs at 127.0.0.11)

Docker uses network namespaces for each container. Then it uses virtual ethernet pair to connect containers together.
















