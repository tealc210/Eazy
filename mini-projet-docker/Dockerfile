FROM mysql:8.0.40-debian AS db

ARG root_password
ARG db_user
ARG db_pwd

ENV MYSQL_ROOT_PASSWORD ${root_password}
ENV MYSQL_USER ${db_user}
ENV MYSQL_PASSWORD ${db_pwd}
ENV MYSQL_DATABASE "db_paymybuddy"

LABEL maintener="DAG"
ADD ./initdb/create.sql /docker-entrypoint-initdb.d/
EXPOSE 3306/tcp

# ------------

FROM maven:3-openjdk-17 AS packager

ARG db_user
ARG db_pwd
ARG db_name
ARG db_instance

ENV MYSQL_INSTANCE ${db_instance}
ENV MYSQL_USER ${db_user}
ENV MYSQL_PASSWORD ${db_pwd}

WORKDIR /usr/src/app
ADD code .
RUN ["mvn", "package"]

#---

FROM amazoncorretto:17-alpine

LABEL maintainer="DAG"

ARG db_user
ARG db_pwd
ARG db_name
ARG db_instance

ENV MYSQL_INSTANCE ${db_instance}
ENV MYSQL_USER ${db_user}
ENV MYSQL_PASSWORD ${db_pwd}

COPY --from=packager /usr/src/app/target/paymybuddy.jar /srv
EXPOSE 8080/tcp
ENTRYPOINT ["java", "-jar", "/srv/paymybuddy.jar"]
