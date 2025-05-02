FROM eclipse-temurin:17-alpine

RUN mkdir /opt/app

ADD spring-rest.jar /opt/app/spring-rest.jar

#Below command will change your current directory to /opt/app
WORKDIR /opt/app

ENTRYPOINT [ "java", "-jar", "/opt/app/spring-rest.jar" ]