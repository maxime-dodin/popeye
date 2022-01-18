FROM maven:3.5-jdk-8-alpine as builder
WORKDIR /worker
COPY pom.xml pom.xml

COPY . .
RUN mvn dependency:resolve
RUN mvn package

FROM openjdk:8-jre-alpine

EXPOSE 80

COPY --from=builder /worker/target/worker-jar-with-dependencies.jar .

CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]