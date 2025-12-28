# Stage 1: Build the JAR
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app

# Copy Maven project files
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

# Stage 2: Run the JAR
FROM eclipse-temurin:17-jre
WORKDIR /app

# Copy built JAR
COPY --from=builder /app/target/*.jar app.jar

# Expose service port
EXPOSE 8080

# Run the app
CMD ["java", "-jar", "app.jar"]
