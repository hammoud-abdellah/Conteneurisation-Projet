# utilisation de l'image maven pour la construction
FROM maven AS build
WORKDIR /app/myapp
COPY . .

RUN mvn clean package -DskipTests

# Image pour ranner le code java
FROM openjdk:17-alpine
WORKDIR /app
 
EXPOSE 8080

COPY --from=build /app/myapp/target/spring-boot-data-jpa*.jar app.jar

ENTRYPOINT ["java","-jar","app.jar"]