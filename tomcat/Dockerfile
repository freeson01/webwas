FROM flyceek/centos7-jdk
RUN mkdir /apps
ADD data/apache-tomcat-8.5.56.tar.gz /apps/
RUN mv /apps/apache-tomcat-8.5.56 /apps/tomcat-8.5.56 \
        && ln -s /apps/tomcat-8.5.56 /apps/tomcat \
        && ln -s /apps/tomcat/conf/setenv.sh /apps/tomcat/bin/setenv.sh \
	&& rm -rf /apps/tomcat/webapps/*

COPY data/ROOT.war /apps/tomcat/webapps/

CMD ["/apps/tomcat/bin/catalina.sh","run"]
