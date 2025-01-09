FROM gradle:7.6.1-jdk17 AS builder
COPY . /app
WORKDIR /app
RUN gradle clean build -x test --no-daemon

FROM openjdk:17-slim
COPY --from=builder /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]