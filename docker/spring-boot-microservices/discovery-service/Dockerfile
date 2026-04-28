FROM eclipse-temurin:21-alpine

#Installing curl command
RUN apk add --update curl
RUN rm -rf /var/cache/apk/*

RUN mkdir /opt/app

ADD discovery-service.jar /opt/app/discovery-service.jar

#Below command will change your current directory to /opt/app
WORKDIR /opt/app

ENTRYPOINT [ "java", "-jar", "discovery-service.jar" ]