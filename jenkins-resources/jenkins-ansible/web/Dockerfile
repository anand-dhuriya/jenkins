FROM  remote-host
 
RUN dnf install epel-release -y && \
    dnf update -y && \
    dnf install -y http://rpms.remirepo.net/enterprise/remi-release-8.rpm && \
    dnf install -y nginx && \
    dnf install -y dnf-plugins-core && \
    dnf module install -y php:remi-7.3 && \
    dnf update -y && \
    dnf install -y                                                          \
      php-fpm                                                               \
      php-cli                                                               \
      php-mysqlnd                                                           \
      php-soap                                                              \
      php-xml                                                               \
      php-zip                                                               \
      php-json                                                              \
      php-mcrypt                                                            \
      php-mbstring                                                          \
      php-zip                                                               \
      php-gd                                                             && \
    mkdir /run/php-fpm                                                   && \
    dnf clean all
 
EXPOSE 80 443
 
VOLUME /var/www/html /var/log/nginx /var/log/php-fpm /var/lib/php-fpm
 
COPY ./conf/nginx.conf /etc/nginx/conf.d/default.conf
 
COPY ./bin/start.sh /start.sh
 
RUN chmod +x /start.sh
 
CMD /start.sh