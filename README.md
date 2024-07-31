# DOCKER 
<a style= witdh:70px height:20px>![image](https://github.com/user-attachments/assets/406f05f5-afd2-4ca4-8844-8b5e3befd7f8)</a>

## Docker Deamon (dockerd): 
> Listens for Docker APIs requests.<br>
> Manages Docker objects such as images, container, networks and volumes.<br>
> Deamon can also communicate with other deamons to manage docker services.<br>

## Docker Client (docker):
> Primary way to interact whith docker.<br>
> Can communicate with more than one deamon.<br> 

!! Docker Desktop includes deamon,client,docker compose and kubernates.

## Docker Registry:
> Stores Docker images.<br>
> Docker Hub is public registry that anyone can use.<br>
> We can run our private registry.<br>

## Images:
> Read-only template with instrucations for creating a Docker Container.<br>
> to build our image, we have to create DockerFile.<br>
> Each instruction in DockerFile creates a layer in the image.<br>
> When we change dockerfile and rebuild image, only those layers which have changed are rebuilt.<br>

## Container:
> Runnable instance of an image.<br>
> We can connet a container to one or more networks.<br>


### In this project, I created a Spring boot project. I will show how to use Docker with Spring Boot project.

1) Create .jar file of the project by using Maven.
   - `mvn clean install` <br>
  After this, the jar file will be created under the target path. Such as `.\spring-boot-docker\target`
     
2) Create a DockerFile
   ```
     FROM openjdk:17 
     ADD target/{JAR_FILE_NAME}.jar app.jar
     ENTRYPOINT [ "java", "-jar","app1.jar" ]
   ```

   > FROM: A docker image can use another image available in the docker registry as its base or parent image. In the above example, we use the openjdk:17 image as our base image.<br>
   
   > ADD: The ADD instruction is used to copy new files and directories to the docker image.<br>
   
   > ENTRYPOINT: This is where you configure how the application is executed inside the container.

4) Build Docker image:
   - go to the path that contains DockerFile and run this command: <br>
   - `docker build -t demo:latest . `<br>
   - The file path `.` defines the location of the Dockerfile in the current directory, and the `-t` argument tags the resulting image, where the repository name is the demo and the tag is the latest<br>

   ! After this, We can check our image is created or not by using `docker images` command.

5) Last step is run docker image in a Container:
   - `docker run -p 8081:8080 demo`

  


