![Java](https://img.shields.io/badge/Java-21-blue?logo=openjdk)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0-brightgreen?logo=springboot)
![Security](https://img.shields.io/badge/OAuth2-JWT-green)

# Spring Authorization Server

Simple OAuth2 Authorization Server built with Spring Boot.

This project provides JWT token generation to secure APIs using OAuth2.


## Overview

- Implements OAuth2 using Spring Authorization Server
- Issues JWT access tokens
- Uses in-memory users and credentials for simplicity


## Running the Application

Run the application:

```
./mvnw spring-boot:run
```

The server will start at http://localhost:9000 


## Running with Kubernetes (optional)

Build the Docker image:

```
./mvnw clean spring-boot:build-image
-Dspring-boot.build-image.imageName=spring-7-auth-server:0.0.1-SNAPSHOT
```

Deploy:

```
kubectl apply -f auth-server-deployment.yaml
kubectl apply -f auth-server-service.yaml
```

Expose:

```
kubectl port-forward svc/auth-server 9000:9000
```

Test:

```
curl http://localhost:9000/.well-known/openid-configuration
```

## Notes

- Ensure the issuer is consistent (`http://auth-server:9000`) when running inside Kubernetes