# docker-houston
presentation for docker-houston meetup

## slides

### slide 1
* Sponsored by The Iron Yard
* Docker & Dockers
* getting introduced
* on Tuesday, July 28th, 2015 @ The Iron Yard

### slide 2
* go to 
* www.webplease.com
* nothing should be there

#### excercise:
```
docker run --name iyard-mysql -e MYSQL_ROOT_PASSWORD=example -d mariadb
docker run --name iyard-wordpress --link iyard-mysql:mysql -p 80:80 -d wordpress
```

* go to  http://www.webplease.com and 
* install wordpress

### slide 3
* What is Docker?
* Technology
* Allows you to package an application with all of its dependencies into a standardized unit for software development.
* Docker containers wrap up a piece of software in a complete filesystem that contains everything it needs to run: 
* This guarantees that it will always run the same, regardless of the environment it is running in.

### slide 4
* Where to get it?
* www.docker.com


### slide 5
* Basic Concepts
* Engine
* Cli
* Image
* Container
* Registry
* Docker Hub


### slide 6
```
Docker CLI
docker search busybox
docker pull busybox
docker run --rm -it --name yard-busy busybox /bin/sh
exit
docker ps -a
docker rm
docker rm -f $(docker ps -aq)

docker run -it --name=yard-ubuntu ubuntu:14.04 /bin/bash

cid=(docker run -itd --name=yard-ubuntu ubuntu:14.04 /bin/bash)

echo $cid
docker inspect $cid
docker history img or cont id
docker start/stop/attach/kill/restart
docker exec
```
#### apache-ex1
apache-dockerfile-ex1
```
FROM ubuntu:14.04

RUN apt-get -y install apache2 

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```
Commands
```
docker build -f apache-dockerfile-ex1 -t apache-ex1 .

docker images

cid=$(docker run -itd apache-ex1)

docker exec $cid ip a

nid=$(docker inspect --format '{{.NetworkSettings.IPAddress}}' $cid)

curl $nid
```
**Caching**
```
docker build -f apache-dockerfile-ex1 -t apache-ex1 .

docker build --no-cache=true -f apache-dockerfile-ex1 -t apache-ex1 .
```
**More Commands ADD and EXPOSE**

#### apache-ex3
apache-dockerfile-ex3
```
FROM ubuntu:14.04

RUN \
  apt-get update && \
  apt-get -y install apache2 

ADD index.html /var/www/html/index.html

EXPOSE 80 

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```

index.html

```
<h1>Docker Rocks!</h1>
```

Commands

```
cat index.html 

docker build -f apache-dockerfile-ex3 -t apache-ex3 .

cid=$(docker run -itd -P apache-ex3)

nid=$(docker inspect --format '{{.NetworkSettings.IPAddress}}' $cid)

curl $nid
```
