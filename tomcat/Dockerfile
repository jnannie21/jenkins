FROM centos

RUN yum update -y \
  && yum install -y java-1.8.0-openjdk \
     java-1.8.0-openjdk-devel \
#     install -y maven \
#     git \
     wget \
#     unzip \
  && yum clean all

#   create tomcat group and tomcat user
RUN groupadd tomcat \
    && useradd -M -s /bin/nologin -g tomcat -d /opt/tomcat tomcat

#   Install Tomcat
RUN wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.72/bin/apache-tomcat-8.5.72.tar.gz \
    && mkdir /opt/tomcat \
    && tar xvf apache-tomcat-8*tar.gz -C /opt/tomcat --strip-components=1

#   copy configurations
COPY tomcat/config/tomcat/*.xml /opt/tomcat/conf/
#COPY config/tomcat/server.xml config/tomcat/web.xml config/tomcat/context.xml config/tomcat/tomcat-users.xml /opt/tomcat/conf/
COPY tomcat/config/tomcat/manager/context.xml /opt/tomcat/webapps/manager/META-INF/context.xml

RUN cd /opt/tomcat \
#    give the tomcat group ownership over /opt/tomcat
    && chgrp -R tomcat /opt/tomcat \
#    give the tomcat group permissions
    && chmod -R g+r conf \
    && chmod g+x conf \
#    make the tomcat user the owner of directories
    && chown -R tomcat webapps/ work/ temp/ logs/

EXPOSE 8085

CMD /opt/tomcat/bin/catalina.sh run
#CMD /opt/tomcat/bin/startup.sh && tail -f /opt/tomcat/logs/catalina.out
