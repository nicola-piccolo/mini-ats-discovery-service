FROM openjdk:12-jdk-alpine

RUN addgroup -S discovery-service && adduser -S discovery-service -G discovery-service

ENV HOME_DIRECTORY="/home/discovery-service"
ENV LOGS_DIRECTORY="$HOME_DIRECTORY/logs"

USER discovery-service:discovery-service

RUN mkdir $LOGS_DIRECTORY

ARG DEPENDENCY=target/dependency

COPY ${DEPENDENCY}/BOOT-INF/lib /app/lib
COPY ${DEPENDENCY}/META-INF /app/META-INF
COPY ${DEPENDENCY}/BOOT-INF/classes /app

ENTRYPOINT ["java","-cp","app:app/lib/*","org.miniats.discoveryservice.DiscoveryServiceApplication"]