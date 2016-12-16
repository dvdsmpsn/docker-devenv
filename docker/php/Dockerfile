FROM centos:7

MAINTAINER Shaun Hare <shaun.hare@nottingham.ac.uk>

#
# Import the Centos-7 RPM GPG key to prevent warnings and Add EPEL Repository
#
RUN rpm --import http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-7 \
    && rpm --import http://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-7 \
    && rpm -Uvh http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-7.rpm

#RUN yum-config-manager --enable remi-php70
RUN yum-config-manager --enable remi-php56

RUN yum -y install \
    mysql-devel \
    mysql-libs \
    mod_ssl \
    php \
    php-fpm \
    php-cli \
    php-mbstring \
    php-mcrypt \
    php-mysql \
    php-xml \
    msmtp \
    && yum -y update bash \
    && rm -rf /var/cache/yum/* \
    && yum clean all


#
# UTC Timezone & Networking
#
RUN ln -sf /usr/share/zoneinfo/UTC /etc/localtime \
    && echo "NETWORKING=yes" > /etc/sysconfig/network



EXPOSE 9000

COPY www.conf /etc/php-fpm.d/www.conf


CMD ["php-fpm","-F"]



#docker run -d -p 80:80 --name centos-php -v $(pwd)../../:/app centos-php nginx -g 'daemon off;'