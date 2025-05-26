FROM eclipse-temurin:17-alpine

#Installing curl command
RUN apk add --update curl
RUN rm -rf /var/cache/apk/*

RUN mkdir /opt/app

ADD customer-service.jar /opt/app/customer-service.jar

#Below command will change your current directory to /opt/app
WORKDIR /opt/app

ENTRYPOINT [ "java", "-jar", "customer-service.jar" ]