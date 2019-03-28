##### Prerequisites
JDK >= 1.8   
GraalVM >= 1.0 RC14 (don't forget to setup GRAALVM_HOME)  
Apache Maven >= 3.5.2  
Docker >= 18.09.3  

##### GOAL
Improve the startup time of a Java application

##### HOW?
Produce a self-contained native executable of the java application, using quarkus maven plugin

##### Run
mvn package -Pnative  
Java standard execution: java -jar 
Native execution: ./target/quarkus-quickstart-runner

##### Benshmark
![Alt text](./quarkus.png?raw=true "Standard Java Execution VS Native Execution")  

Native startup  is more fast (146 times) than standard startup  
Native code size >> Java byte (.class)  code  
Native file is a self-contained code (doesn't need jvm to be executed)  
Native code doesn't mean binary machine code  


##### Dockerize native executable
The previously generated native code is your local-os compatible, thus the docker image could not be portable (in other os).  

To avoid such situation, we will tell the Maven build to produce "the  executable" using a "conventional os" (using a Docker container):  
mvn clean package -Pnative -Dnative-image.docker-build=true  

Similarly, this "conventional os" is used as base container, from which the final docker image of our native code will be created.  
In this example: the "conventional os" is fedora/centos (check: getting-started/src/main/docker/Dockerfile):   

docker build -f src/main/docker/Dockerfile -t quarkus-quickstart/quickstart .  
docker run -i --rm -p 8080:8080 quarkus-quickstart/quickstart

##### Ref
https://quarkus.io/


