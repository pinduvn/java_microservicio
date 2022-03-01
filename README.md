# Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/2.6.2/maven-plugin/reference/html/)
* [Create an OCI image](https://docs.spring.io/spring-boot/docs/2.6.2/maven-plugin/reference/html/#build-image)
* [Spring Web](https://docs.spring.io/spring-boot/docs/2.6.2/reference/htmlsingle/#boot-features-developing-web-applications)

### Guides
The following guides illustrate how to use some features concretely:

* [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
* [Serving Web Content with Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* [Building REST services with Spring](https://spring.io/guides/tutorials/bookmarks/)


## Para compilar el proyecto en un **`jar`**
```sh
docker run -it --rm --name pindu-mvn \
    -v "$(pwd)/.m2":/root/.m2 \
    -v "$(pwd)":/usr/src/mymaven \
    -w /usr/src/mymaven maven:3.3-jdk-8 mvn clean install
```

## Para correr el proyecto
```sh
docker run -it --rm --name pindu-mvn \
    -p 8080:8080 \
    -v "$(pwd)/.m2":/root/.m2 \
    -v "$(pwd)":/usr/src/mymaven \
    -w /usr/src/mymaven maven:3.3-jdk-8 mvn package && \
    java -jar target/demo-0.0.1-SNAPSHOT.jar
```

## Para correr los test
```sh
docker run -it --rm --name pindu-mvn \
    -p 8080:8080 \
    -v "$(pwd)/.m2":/root/.m2 \
    -v "$(pwd)":/usr/src/mymaven \
    -w /usr/src/mymaven maven:3.3-jdk-8 mvn test
```
## Para ver las publicaciones cargadas
[http://localhost:8080/api/tutorials](http://localhost:8080/api/tutorials)

## Para acceder a la base de datos con las siguientes credenciales.
```
spring.datasource.username=sa
spring.datasource.password=password
```

[http://localhost:8080/h2-console](http://localhost:8080/h2-console)

## Para cargar una nueva publicacion
```sh
curl -X POST http://localhost:8080/api/tutorials \
    -H 'Content-Type: application/json' \
    -d '{"title":"Prueba 3","description":"Prueba 3"'}
```