FROM alpine/git
WORKDIR /discovery-app
RUN git clone https://github.com/reeshabh90/Discovery-server.git


FROM maven:3.5-jdk-8-alpine
WORKDIR /discovery-app
COPY --from=0 /discovery-app/Discovery-server /discovery-app
RUN mvn install


FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAVA_OPTS
ENV JAVA_OPTS=$JAVA_OPTS
WORKDIR /discovery-app
COPY --from=1 /discovery-app/target/discovery-server-0.0.1-SNAPSHOT.jar /discovery-app
EXPOSE 8761
ENTRYPOINT exec java $JAVA_OPTS -jar discovery-server-0.0.1-SNAPSHOT.jar
# For Spring-Boot project, use the entrypoint below to reduce Tomcat startup time.
#ENTRYPOINT exec java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar docker.jar
