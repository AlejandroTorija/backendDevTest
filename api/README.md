# Backend Dev Test

## Technologies

* Spring Boot (v3.0.8)
* Maven (v3.6.3)
* Java (v17)
* Mapstruct (v1.5.3.Final)
* Lombok
* OpenAPI (v2.0.2)
* Jacoco (v0.8.8)
* JUnit (v5.9.2)
* Mockito (v5.2.0)

## Description

Api Rest that exposes an Endpoint in charge of returning similar products. These products are obtained based on the product ID indicated as PathVariable in the call to the Endpoint.

### Project structure

#### Repository

The repository layer has interface segregation and is responsible for making the corresponding calls to the other available endpoints through the use of RestTemplate.

#### Service

The service layer also has segregation of interfaces and is divided into two services, the first one connects with the repository layer and the second one connects with the first one.

#### Controller

The controller layer is responsible for exposing the endpoint that obtains similar products through the first service.

#### Model, Dto & Mapper

It uses both a model that will be used by the repository layer and the second service and a dto that will be used by the first service to return it through the endpoint. For the conversion between model and dto we use a mapper that uses mapstruct for it.

### Request example

http://localhost:5000/product/1/similar

## Use

### Deploy to docker container

```shell
docker-compose up -d --build
```

### Execute using the JVM

```shell
mvn clean install
java -jar similar-products-be-test-0.0.1-SNAPSHOT.jar
```

### Access OpenApi interface

http://localhost:5000/swagger-ui/index.html

## Test

### Unit Tests

Unit tests have been added, so that they can be executed:

```shell
mvn test
```

### Code coverage

Jacoco has been added to be able to view test coverage. 

We will be able to see the results by accessing the file auto-generated by jacoco in the following route:

*./target/site/jacoco/index.html*