## Prerequisites
JDK >= 1.8   
GraalVM >= 1.0 RC14 (don't forget to setup GRAALVM_HOME)  
Apache Maven >= 3.5.2  
Docker >= 18.09.3  

## GOAL
Improves the startup time of a Java application

## HOW?
Produce a self-contained native executable of the java application, using quarkus maven plugin

## Run
mvn package -Pnative  
Java standard execution: java -jar 
Native execution: ./target/quarkus-quickstart-runner

## Benshmark
![Alt text](./media/quarkus.png?raw=true "Standard Java Execution VS Native Execution")  

Native startup  is more fast (146 times) than standard startup  
Native code size >> Java byte (.class)  code  
Native file is a self-contained code (doesn't need jvm to be executed)  
Native code doesn't mean binary machine code  


## Dockerize native executable
 

