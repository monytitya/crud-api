# Base image with JDK 17
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

# Copy Maven wrapper & pom.xml
COPY mvnw .
COPY pom.xml .

# Download dependencies
RUN ./mvnw dependency:go-offline -B

# Copy source code
COPY src ./src

# Build project
RUN ./mvnw clean package -DskipTests

EXPOSE 8090

CMD ["java", "-jar", "target/crud-api-0.0.1-SNAPSHOT.jar"]
