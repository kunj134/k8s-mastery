FROM maven AS builder
COPY . /sa-webapp
WORKDIR /sa-webapp
RUN mvn install
#COPY src /sa-webapp/src

ENV SA_LOGIC_API_URL http://localhost:5000

FROM openjdk:8-jre-alpine
COPY --from=builder /sa-webapp/target/sentiment-analysis-web-0.0.1-SNAPSHOT.jar ./
EXPOSE 8080
CMD ["java", "-jar", "sentiment-analysis-web-0.0.1-SNAPSHOT.jar", "--sa.logic.api.url=${SA_LOGIC_API_URL}"]

#
#FROM maven:3.5-jdk-8-alpine AS builder
#COPY pom.xml /sa-webapp/pom.xml
#WORKDIR sa-webapp
#RUN mvn clean package && mvn clean install spring-boot:repackage
#COPY src /sa-webapp/src

#ENV SA_LOGIC_API_URL http://localhost:5000

#FROM openjdk:8-jre-alpine
#COPY --from=builder /sa-webapp/target/sentiment-analysis-web-0.0.1-SNAPSHOT.jar ./
#EXPOSE 8080
#CMD ["java", "-jar", "sentiment-analysis-web-0.0.1-SNAPSHOT.jar", "--sa.logic.api.url=${SA_LOGIC_API_URL}"]
