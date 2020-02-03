# Microservices-docker-deployment
A repository with Docker Compose and Docker to build and deploy Microservices


The File Structure contains Dockerfiles of respective Spring Microservices including Discovery Server and respective clients which register to this server and are connected through a network create by Docker Compose at run time.


Note: The main idea behind this architecture is: The respective Spring microservices can be developed independently. All one has to do is to clone the repositories with respective Dockerfile and run within a container using Docker Compose.
