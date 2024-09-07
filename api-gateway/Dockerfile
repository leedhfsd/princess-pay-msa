# Use an official OpenJDK runtime as a parent image
FROM openjdk:17-jdk-alpine AS build

# Set the working directory in the container
WORKDIR /app

# Copy the Gradle wrapper and build files
COPY gradlew /app/
COPY gradle /app/gradle
COPY build.gradle /app/
COPY settings.gradle /app/

# Copy source code
COPY src /app/src

# Make Gradle wrapper executable
RUN chmod +x gradlew

# Build the application
RUN ./gradlew build

# Use a smaller base image for the final stage
FROM openjdk:17-jdk-alpine

# Set the working directory in the container
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/build/libs/*.jar app.jar

EXPOSE 8765

ENTRYPOINT ["java", "-jar", "app.jar"]
