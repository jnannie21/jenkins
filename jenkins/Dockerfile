FROM jenkins/jenkins

USER root

RUN apt update -y \
     && apt install -y maven \
#     git \
#     wget \
  && apt clean all

EXPOSE 8080

#CMD tail -f /dev/null