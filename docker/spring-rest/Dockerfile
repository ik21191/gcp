FROM eclipse-temurin:17-alpine

RUN mkdir /opt/app

ADD spring-rest.jar /opt/app/spring-rest.jar

#Below command will change your current directory to /opt/app
WORKDIR /opt/app

#Installing curl command
RUN apk add --update curl
RUN rm -rf /var/cache/apk/*

ENTRYPOINT [ "java", "-jar", "spring-rest.jar" ]