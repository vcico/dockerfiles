# nginx + php-fpm 搭建PHP环境



	$ docker pull nginx:latest
	$ docker build -t phpfpm:v0.1   # 来自phpfpm文件夹
	$ docker run -d --name phpfpm  -v /home/data:/home/data phpfpm:v0.1
	$ docker run -d -p 80:80 --name nginx -v /home/data:/home/data --link phpfpm:phpfpm nginx:latest
	
	
	
>  配置

	修改 php-fpm 配置的 listen  (phpfpm文件夹下  build时已经改为 0.0.0.0:9000)
	修改nginx配置 的  root 和 fastcgi_param
	网站根目录改在了 /data/www
	nginx的日志 error_log  access_log  改在了 /data/log/nginx
	
	
	
> 注意事项

	nginx 不保留日志
	
	lrwxrwxrwx. 1 root root 11 Nov  4 18:41 access.log -> /dev/stdout
	lrwxrwxrwx. 1 root root 11 Nov  4 18:41 error.log -> /dev/stde