FROM mysql:8.0.40-debian AS db

LABEL maintener="DAG"

ADD ./initdb/create.sql /docker-entrypoint-initdb.d/
EXPOSE 3306/tcp

# ------------

# FROM maven:3-openjdk-17 AS packager

# ARG db_user
# ARG db_pwd
# ARG db_name
# ARG db_instance

# ENV MYSQL_INSTANCE ${db_instance}
# ENV MYSQL_USER ${db_user}
# ENV MYSQL_PASSWORD ${db_pwd}

# WORKDIR /usr/src/app
# ADD code .
# RUN ["mvn", "package"]

#---

FROM amazoncorretto:17-alpine AS app

LABEL maintainer="DAG"

RUN mkdir -p /config

COPY startup/application.properties startup/export.sh /config/
COPY startup/paymybuddy.jar /srv/
EXPOSE 8080/tcp
CMD [ "/config/export.sh ]
ENTRYPOINT ["java", "-Dspring.config.location=/config/application.properties", "-jar", "/srv/paymybuddy.jar"]
