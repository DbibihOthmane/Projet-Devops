# Stage 1: Build the JAR
FROM maven:3.8.5-openjdk-17 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Create the runtime image
FROM openjdk:17-jdk-alpine
WORKDIR /app
COPY --from=builder /app/target/ProjectManagementsSystem-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 9192
ENTRYPOINT ["java", "-jar", "app.jar"]
