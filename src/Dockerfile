FROM ubuntu:latest AS build
LABEL authors="rafael"

RUN apt-get update
RUN apt-get install -y openjdk-17

COPY . .

RUN apt-get install maven -y
RUN mvn clean install

FROM openjdk:17-alpine

EXPOSE 8080

COPY --from=build /target/todolist-0.0.1-SNAPSHOT.jar app.jar

ENTRYPOINT [ "java", "-jar", "app.jar" ]