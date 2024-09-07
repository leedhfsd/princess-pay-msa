# Use an official OpenJDK runtime as a parent image
FROM openjdk:17.0.1-jdk AS build

# Set the working directory in the container
WORKDIR /app

# Make Gradle wrapper executable
RUN chmod +x gradlew

# Build the application
RUN ./gradlew build

# Use a smaller base image for the final stage
FROM openjdk:17.0.1-jdk

# Set the working directory in the container
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/build/libs/*.jar app.jar

EXPOSE 8100

ENTRYPOINT ["java", "-jar", "app.jar"]
