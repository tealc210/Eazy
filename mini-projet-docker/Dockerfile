FROM mysql:8.0.40-debian AS db

ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_USER="smb-admin"
ENV MYSQL_PASSWORD="irbeoibeoijge"
ENV MYSQL_DATABASE="db_paymybuddy"
ADD initdb/create.sql /docker-entrypoint-initdb.d
EXPOSE 3306/tcp

#---

FROM maven:3-openjdk-17 AS packager

MAINTAINER DAG
ENV DATABASE_HOST="172.17.0.2"
ENV DATABASE_USER="smb-admin"
ENV DATABASE_PASS="irbeoibeoijge"
WORKDIR /usr/src/app
ADD code .
RUN ["mvn", "package"]

#---

FROM amazoncorretto:17-alpine

ENV DATABASE_HOST="172.17.0.2"
ENV DATABASE_USER="smb-admin"
ENV DATABASE_PASS="irbeoibeoijge"
COPY --from=packager /usr/src/app/target/paymybuddy.jar /srv
EXPOSE 8080/tcp
ENTRYPOINT ["java", "-jar", "/srv/paymybuddy.jar"]
