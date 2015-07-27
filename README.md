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
* 

### slide 5
