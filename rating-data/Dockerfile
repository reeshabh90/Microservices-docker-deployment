FROM alpine/git
RUN apk --no-cache add curl
WORKDIR /rating-data-app
RUN git clone https://github.com/reeshabh90/rating-data.git

FROM maven:3.5-jdk-8-alpine
WORKDIR /rating-data-app
COPY --from=0 /rating-data-app/rating-data /rating-data-app
RUN mvn install

FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAVA_OPTS
ENV JAVA_OPTS=$JAVA_OPTS
WORKDIR /rating-data-app
COPY --from=1 /rating-data-app/target/rating-data-0.0.1-SNAPSHOT.jar /rating-data-app
EXPOSE 8082
ENTRYPOINT exec java $JAVA_OPTS -jar rating-data-0.0.1-SNAPSHOT.jar