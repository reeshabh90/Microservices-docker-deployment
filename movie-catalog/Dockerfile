FROM alpine/git
RUN apk --no-cache add curl
WORKDIR /movie-catalog-app
RUN git clone https://github.com/reeshabh90/movie-catalog.git

FROM maven:3.5-jdk-8-alpine
WORKDIR /movie-catalog-app
COPY --from=0 /movie-catalog-app/movie-catalog /movie-catalog-app
RUN mvn install

FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAVA_OPTS
ENV JAVA_OPTS=$JAVA_OPTS
WORKDIR /movie-catalog-app
COPY --from=1 /movie-catalog-app/target/movie-catalog-0.0.1-SNAPSHOT.jar /movie-catalog-app
EXPOSE 8083
ENTRYPOINT exec java $JAVA_OPTS -jar movie-catalog-0.0.1-SNAPSHOT.jar