FROM mysql:8.0.40-debian AS db

LABEL maintener="DAG"

EXPOSE 3306/tcp

#---

FROM amazoncorretto:17-alpine AS app

LABEL maintainer="DAG"

COPY startup/paymybuddy.jar startup/application.properties /srv/
EXPOSE 8080/tcp
ENTRYPOINT ["java", "-jar", "/srv/paymybuddy.jar"]
