FROM maven:3.9.6-eclipse-temurin-21-alpine AS builder

WORKDIR /build

COPY . .
RUN mvn dependency:resolve
RUN mvn package

FROM eclipse-temurin:21-jre-alpine

WORKDIR /app

COPY --from=builder /build/target/worker-jar-with-dependencies.jar ./worker-jar-with-dependencies.jar

CMD [ "java", "-jar", "worker-jar-with-dependencies.jar" ]