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

* docker run --name iyard-mysql -e MYSQL_ROOT_PASSWORD=example -d mariadb
* docker run --name iyard-wordpress --link iyard-mysql:mysql -p 80:80 -d wordpress
* go to http://www.webplease.com and install wordpress

