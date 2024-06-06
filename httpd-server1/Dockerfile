# Retrieve Httpd Server version: Apache/2.4.59 (Unix)
FROM httpd

RUN su

# Install wget
RUN apt-get update && apt-get install -y wget

# Download tomcat connector
RUN mkdir -p /var/mod_jk && cd /var/mod_jk && wget https://archive.apache.org/dist/tomcat/tomcat-connectors/jk/tomcat-connectors-1.2.49-src.tar.gz

# Unzip
RUN cd /var/mod_jk && tar -xvf tomcat-connectors-1.2.49-src.tar.gz && mv tomcat-connectors-1.2.49-src tomcat-connectors-1.2.49

# Install toolchain
RUN apt-get update && apt-get install -y apache2-dev gcc g++ make libtool

# Build tomcat connector
RUN cd /var/mod_jk/tomcat-connectors-1.2.49/native && ./configure --with-apxs=/usr/bin/apxs2 && make

# Copy binary
RUN cp /var/mod_jk/tomcat-connectors-1.2.49/native/apache-2.0/mod_jk.so /usr/local/apache2/modules

#  Copy config file
COPY ./httpd.conf /usr/local/apache2/conf/

# Copy worker file
COPY ./workers.properties /usr/local/apache2/conf/