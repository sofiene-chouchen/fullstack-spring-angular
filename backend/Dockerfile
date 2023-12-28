#1st Stage
FROM maven:3.6.3-openjdk-11 as build-stage
WORKDIR /app
COPY pom.xml /app/
RUN mvn dependency:go-offline -B
COPY src /app/src
RUN mvn package -DskipTests

#2nd Stage to add change
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=build-stage /app/target/ecommerce-0.0.1-SNAPSHOT.war /app/
EXPOSE 8080
CMD ["java", "-jar", "ecommerce-0.0.1-SNAPSHOT.war"]
