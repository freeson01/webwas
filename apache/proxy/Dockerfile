FROM flyceek/centos7-jdk

RUN yum -y install gcc g++ gcc-c++ make perl pcre-devel \
	&& mkdir -p /apps \
	&& mkdir /data
#COPY data/httpd-2.4.46.tar.gz /data/
#ADD data/httpd-2.4.46.tar.gz /data/
ADD data/* /data/
#RUN tar xvf /data/httpd-2.4.46.tar.gz -C /data/ \
RUN cd /data/httpd-2.4.46 \
        && ./configure --prefix=/apps/apache2.4.46 --with-included-apr --with-included-apr-util --enable-mods-shared=all --with-mpm=event \
        && make \
        && make install \
	&& rm -rf /apps/apache2.4.46/conf/httpd.conf \
	&& cp /data/httpd.conf /apps/apache2.4.46/conf/ \
	&& cp /data/mime.types /apps/apache2.4.46/conf/ \
	&& cd /data/tomcat-connectors-1.2.48-src/native \
        && ./configure --with-apxs=/apps/apache2.4.46/bin/apxs \
        && make \
        && make install

#COPY data/httpd.conf /apps/apache2.4.46/conf/
#	&& data/mime.types /apps/apache2.4.46/conf/

#ADD tomcat-connectors-1.2.48-src.tar.gz /data/
#RUN cd /data/tomcat-connectors-1.2.48-src/native \
#	&& ./configure --with-apxs=/apps/apache2.4.46/bin/apxs \
#	&& make \
#	&& make install
#COPY data/workers.properties /apps/apache2.4.46/conf/

CMD ["/apps/apache2.4.46/bin/apachectl" , "-D" , "FOREGROUND"]
