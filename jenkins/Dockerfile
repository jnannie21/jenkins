FROM jenkins/jenkins

USER root

RUN apt update -y \
     && apt install -y maven \
  && apt clean all

COPY ./jenkins/config/maven/settings.xml /usr/share/maven/conf/settings.xml

EXPOSE 8080
