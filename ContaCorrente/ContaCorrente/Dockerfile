# FROM openjdk:17-jdk-slim
# ARG JAR_FILE=target/*.jar
# COPY ${JAR_FILE} app.jar
# ENTRYPOINT ["java","-jar", "/app.jar"]

FROM maven:3.8.4-openjdk-17-slim AS build
WORKDIR /app

COPY src /app/src
COPY pom.xml /app

RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-slim
COPY --from=build /app/target/*.jar app/app.jar
WORKDIR /app

EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
