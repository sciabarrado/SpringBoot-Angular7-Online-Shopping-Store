FROM openjdk:11-oracle as builder
USER root
COPY mvnw pom.xml /root/
COPY src /root/src
COPY .mvn /root/.mvn
WORKDIR /root
RUN bash mvnw package -DskipTests 
FROM openjdk:11-oracle
WORKDIR /
VOLUME /tmp
COPY --from=builder /root/target/*.jar app.jar
ENTRYPOINT ["java", "-jar","/app.jar", "--spring.profiles.active=do"]
