# Use official OpenJDK replacement
FROM eclipse-temurin:17-jdk-jammy

WORKDIR /app

# Copy Maven wrapper and pom.xml first (for Docker cache)
COPY mvnw pom.xml ./
COPY .mvn/ .mvn/

# Download dependencies
RUN chmod +x mvnw && ./mvnw dependency:go-offline -B

# Copy source code
COPY src ./src

# Build the application
RUN ./mvnw clean package -DskipTests

# Expose Spring Boot port
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "target/smart-rental-backend-1.0.0.jar"]
