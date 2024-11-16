FROM amazoncorretto:17-alpine

RUN apt-get update && apt-get install maven apt install openjdk-17-jdk-headless -y
COPY target/paymybuddy.jar /srv/ 
EXPOSE 8080/tcp
CMD ['java', '-jar', '/srv/paymybuddy.jar']

FROM mysql:8.0.40-debian

RUN mkdir /data
EXPOSE 3306/tcp
