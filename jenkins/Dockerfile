FROM centos

MAINTAINER Sonu

RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*


RUN mkdir /opt/tomcat/

WORKDIR /opt/tomcat
RUN curl -O https://downloads.apache.org/tomcat/tomcat-8/v8.5.87/bin/apache-tomcat-8.5.87.tar.gz
RUN tar xvfz apache*.tar.gz
RUN mv apache-tomcat-8.5.87/* /opt/tomcat/.
RUN yum -y install java
RUN java -version

WORKDIR /opt/tomcat/webapps
COPY /var/lib/jenkins/workspace/Test-Jobs/java-application/target/. /opt/tomcat/webapps

EXPOSE 80

CMD ["/opt/tomcat/bin/catalina.sh", "run"]
