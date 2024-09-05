# Use an official OpenJDK runtime as a parent image
FROM openjdk:17.0.1-jdk

# Set the working directory in the container
WORKDIR /app

# Copy the JAR file to the container
COPY build/libs/*.jar app.jar

EXPOSE 8100

ENTRYPOINT ["java", "-jar", "app.jar"]
