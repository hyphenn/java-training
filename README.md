# Training - boot setup

## Overview
This repo was created for Spring-Boot training purpose. It includes Tomcat, MySQL and MongoDB docker-compose file and Spring Boot sample project with mvn-tomcat-plugin preconfigured. Created containers will store the data in container volumes created for that purpose. They can be safely removed without any risk of loosing generated data. Containers will restart automatically on docker daemon boot.
Default Java project deployment configuration remains in pom.xml and is directly linked to ./tomcat/tomcat-users.xml

### Versions
  + Apache Tomcat/8.0.53
  + MySQL 8.0.12
  + MongoDB 4.0
  + OpenJDK version 1.8.0_181 64bit
  + Spring Boot 2.0.6
  
### Default users
For MySQL qnd MongoDB you can change the default users directly in the docker-compose.yml file. For Tomcat you should modify ./tomcat/tomcat-users.xml. 

### Volumes
  + mysql-volume bind to container's /var/lib/mysql
  + mongodb_volume bind to container's /data/db
  + tomcat-volume bind to container's /usr/local/tomcat

### Default exposed ports
  + 80 - Tomcat
  + 1337 - Tomcat debugging
  + 3306 - MySQL
  + 22017 - MongoDB
  + 8081 - MySQL client Adminer
  + 8082 - MongoDB client Mongo-Express
  
### Useful commands
```shell
#create container in detached mode and deploy your app
docker-compose up -d 
mvn tomcat7:deploy
#### debugging + misc

#connect to existing container 
docker exec -it my_container /bin/bash

#attach to existing container 
docker attach my_container

#tear down docker containers
docker-compose down


#cleaning up the mess - ATTENTION : removes unused volumes and networks i.e not linked to any container
docker network prune
docker volume inspect my_volume
```
