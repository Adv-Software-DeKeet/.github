# Docker

Docker Hub is a cloud-based registry that allows you to store and share Docker images. Docker images are essentially pre-built container images that include your application code and its dependencies. With Docker Hub, you can push your Docker images to the cloud and share them with other developers or deploy them to production environments.

### Create container

To create a container we need a Dockerfile e.g. for my UserService:

```
FROM openjdk:19-jdk-alpine
MAINTAINER JoviSimons
COPY target/UserService-0.0.1-SNAPSHOT.jar UserService-0.0.1-SNAPSHOT.jar
ENTRYPOINT ["java","-jar","/UserService-0.0.1-SNAPSHOT.jar"]FROM openjdk:19-jdk-alpine
```

It uses the .jar file that is created in the following GitAction:

```
name: Java CI with Maven

on:
  push:
    branches:
      - master

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - name: Set up JDK 19
        uses: actions/setup-java@v3
        with:
          java-version: '19'
          distribution: 'temurin'
          cache: maven
      - name: Build with Maven
        run: mvn clean install
      - name: Publish to Docker Hub
        uses: docker/build-push-action@v1
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_PASSWORD }}
          repository: jovisimons/dekeet-userservice
          tags: latest
```
When pushed on master it runs the command ```mvn clean install```, which creates the .jar we use in the Dockerfile and uploaded to dockerhub. 

