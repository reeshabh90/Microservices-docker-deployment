FROM alpine/git
RUN apk --no-cache add curl
WORKDIR /movie-info-app
RUN git clone https://github.com/reeshabh90/movie-info.git

FROM maven:3.5-jdk-8-alpine
WORKDIR /movie-info-app
COPY --from=0 /movie-info-app/movie-info /movie-info-app
RUN mvn install

FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAVA_OPTS
ENV JAVA_OPTS=$JAVA_OPTS
WORKDIR /movie-info-app
COPY --from=1 /movie-info-app/target/movie-info-0.0.1-SNAPSHOT.jar /movie-info-app
EXPOSE 8081
ENTRYPOINT exec java $JAVA_OPTS -jar movie-info-0.0.1-SNAPSHOT.jar