# Build stage
FROM maven:3-openjdk-17 AS build
WORKDIR /app

# Copy source code vào image
COPY . .

# Build ứng dụng
RUN mvn clean package -DskipTests

# Run stage
FROM openjdk:17-jdk-slim
WORKDIR /app

# Copy file WAR đã build từ bước trước
COPY --from=build /app/target/UNIME.war unime.war

# Expose cổng 8080 cho ứng dụng
EXPOSE 8080

# Chạy ứng dụng
ENTRYPOINT ["java", "-jar", "unime.war"]
