FROM centos

USER root

RUN yum update -y \
  && yum install -y java-1.8.0-openjdk \
     java-1.8.0-openjdk-devel \
     wget \
  && yum clean all

RUN wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.72/bin/apache-tomcat-8.5.72.tar.gz \
    && mkdir /opt/tomcat \
    && tar xvf apache-tomcat-8*tar.gz -C /opt/tomcat --strip-components=1

COPY ./tomcat/config/*.xml /opt/tomcat/conf/
COPY ./tomcat/config/manager/context.xml /opt/tomcat/webapps/manager/META-INF/context.xml

EXPOSE 8085
