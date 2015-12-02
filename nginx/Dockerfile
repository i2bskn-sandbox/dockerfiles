FROM centos:centos7

MAINTAINER i2bskn <i2bskn@gmail.com>

RUN yum -y update; yum clean all
RUN yum -y install \
    wget \
    tar \
    openssl-devel \
    pcre-devel \
    gcc \
    make; \
    yum clean all

WORKDIR /usr/local/src
RUN wget http://nginx.org/download/nginx-1.8.0.tar.gz \
    && tar zxvf nginx-1.8.0.tar.gz \
    && rm -f nginx-1.8.0.tar.gz

WORKDIR /usr/local/src/nginx-1.8.0
RUN ./configure \
    --prefix=/usr/local/nginx \
    --with-http_ssl_module \
    --with-http_gzip_static_module \
    --with-http_stub_status_module \
    && make \
    && make install

ADD nginx.conf /usr/local/nginx/conf/nginx.conf
ADD conf.d /usr/local/nginx/conf/conf.d

EXPOSE 80 443

CMD ["/bin/bash"]
