# Spring Boot Microservices
This application demonstrates the working of microservices in Spring Boot. The `application.properties` files are present in each microservice. We are not using these `application.properties` for building or running the applications; these are only used to show which properties are used while building the images. The source code of these microservices is present at this GitHub location: [source-code](https://github.com/ik21191/spring-boot-microservice).

To spin up all the applications, run the below command.

```
docker-compose up -d
```

**Note:-** Do not run the above command again; instead, use the below commands to `stop` and `start`.

**Stop:** Run `docker-compose stop`

**Start:** Run `docker-compose start`

## Discovery Service or Service Registry
Service discovery in Spring Boot microservices is a mechanism that allows services to find and communicate with each other dynamically without hardcoding network locations (IP addresses and ports). 

It is a centralized database where all service instances register their network locations upon startup.

In this microservice example, `Eureka Server(Netflix Eureka)` is used as a `Discovery Service` or `Service Registry`. You can use this [eureka-server](http://localhost:8761/) to access `Eureka Server`.

## Gateway Service
A gateway service (API gateway) in microservices acts as a single, centralized entry point for all client requests, routing them to the appropriate backend services.

In this microservice example, `Spring Cloud Gateway` is used as a gateway service.

You can use this [gateway server](http://localhost:8080/actuator/info) to access `Gateway Server`.

## Customer Service
This is the first microservice in this demo application.

There are two ways to access customer service.

- Via the customer service application directly using this link: [customer-service-url-1](http://localhost:3001/customers/ping).

- Via Gateway Service using this link:  [customer-service-url-2](http://localhost:8080/customers/ping).

All available REST endpoints are present in this controller, [customer-controller](https://github.com/ik21191/spring-boot-microservice/blob/main/customer-service/src/main/java/com/example/customerservice/CustomerController.java).

## Order Service
This is the second microservice in this demo application, where all REST endpoints are secured. You can use below credentials to acesss the resources.

**user** `test`

**password** `test`

There are two ways to access the Order Service.

- Via the Order Service application directly using this link: [order-service-url-1](http://localhost:3002/orders/ping). 

- Via Gateway Service using this link:  [order-service-url-2](http://localhost:8080/orders/ping).

All available REST endpoints are present in this controller: [order-controller](https://github.com/ik21191/spring-boot-microservice/blob/main/order-service/src/main/java/com/example/orderservice/OrderController.java).