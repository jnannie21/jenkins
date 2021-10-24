FROM jenkins/jenkins

USER root

RUN apt update -y \
     && apt install -y maven \
  && apt clean all

EXPOSE 8080
