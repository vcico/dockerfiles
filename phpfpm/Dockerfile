# 一个简单的php-fpm
# -F nodaemonize 非守护进程
# 

FROM ubuntu:14.04

RUN apt-get update	\
	&& apt-get install -y wget gcc make  libxml2-dev libpng12-dev libjpeg-dev libcurl4-openssl-dev	\
	&& wget -O php-7.1.11.tar.gz http://hk1.php.net/get/php-7.1.11.tar.gz/from/this/mirror	\
	&& tar -zxvf php-7.1.11.tar.gz \
	&& cd php-7.1.11	\
	&& ./configure --with-openssl --with-curl --with-gd --enable-mbstring --enable-fpm --with-iconv --with-fpm-user=www-data --with-fpm-group=www-data --with-libxml-dir --with-mysqli --with-pdo-mysql --with-mhash  \
	&& make && make install 	\
	&& rm -rf /var/lib/apt/lists/* \ 
	&& cd ../	\
	&& rm  php-7.1.11.tar.gz \
	&& rm -r php-7.1.11 \
	&& apt-get purge -y --auto-remove wget gcc make
	
COPY ./php.ini /usr/local/lib/
COPY ./php-fpm.conf   /usr/local/etc/
COPY ./www.conf  /usr/local/etc/php-fpm.d/
	
CMD ["/usr/local/sbin/php-fpm", "-F", "-c", "/usr/local/lib/php.ini",  "-y", "/usr/local/etc/php-fpm.conf"]





	
	

	