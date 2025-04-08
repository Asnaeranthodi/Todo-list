# Stage 1: Build using Maven
FROM maven:3.9.4-eclipse-temurin-17 AS build

# Set working directory inside container
WORKDIR /app

# Copy all necessary files
COPY . .

# Build the project and skip tests (optional)
RUN mvn clean install -DskipTests

# Stage 2: Create minimal runtime image
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

# Copy the built jar file from previous stage
COPY --from=build /app/target/*.jar app.jar

# Expose the port your app runs on (change if different)
EXPOSE 8080

# Command to run the app
ENTRYPOINT ["java", "-jar", "app.jar"]

