FROM ubuntu:22.04

# Step 2 : Add the metadata to the image
LABEL maintainer="raghu@123.com"
LABEL version="1.0"
LABEL description="A simple Java application using OpenJDK 17"

# Step 3: Build time variable
ARG version=1.0

# Step 4: Set environment variables
ENV APP_HOME=/app
ENV JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64

# Step 5: Set the working directory
WORKDIR $APP_HOME

# Step 6: Update package lists
RUN apt update && apt install openjdk-21-jdk wget -y

#Step 7: Download the application JAR file
RUN wget "https://storage.googleapis.com/newbucketforspring/spring-petclinic-3.5.0-SNAPSHOT.jar"


# Step 8: Add the user to run the application
RUN useradd -ms /bin/bash raghu

# Step 9: Switch to the non-root user
USER raghu

# Step 10: Expose the Application
EXPOSE 8080

# Step 11: Command to run the application
CMD ["java", "-jar", "spring-petclinic-3.5.0-SNAPSHOT.jar"]
