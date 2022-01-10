---
layout: default
title: Nginx Template
nav_order: 4
has_children: true
parent: Nginx
---

# Nginx Template
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}



---
## Template web static.

Create config file for web static. E.g: ReactJS
{: .no_toc }

```bash

server {
  listen 80;
  server_name _ ;
  # ssl_certificate /etc/ssl/file.pem;
  # ssl_certificate_key /etc/ssl/private/file.pem;
  #       ssl_protocols       TLSv1 TLSv1.1 TLSv1.2;
  #	add_header Strict-Transport-Security "max-age=31536000; includeSubDomains";

  root /var/www/welcome/build;
  index index.html index.htm index.nginx-debian.html;


  location / {
    root /var/www/welcome/build;
    index index.html index.nginx-debian.html;
    if ( $uri = '/index.html' ) {
      add_header Cache-Control no-store always;
    }
    try_files $uri $uri/ /index.html;
  }
}
```

## Template config PHP (Laravel)
```sh
server {
        listen   80; ## listen for ipv4; this line is default and implied

        index index.php index.html index.htm;

        # Make site accessible from http://localhost/
        server_name yourdomain.com; 
        access_log /var/log/nginx/yourWebsite_access.log;
        error_log /var/log/nginx/yourWebsite_error.log;
        set $root_path '/data/yourPathWebsite/public';
        root $root_path;
	      client_max_body_size 16M;
        try_files $uri $uri/ @rewrite;

        location @rewrite {
            rewrite ^/(.*)$ /index.php?_url=/$1;
        }

        location ~ \.php$ {
                try_files $uri =404;
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini

                # With php5-cgi alone:
                fastcgi_read_timeout 150;
                #fastcgi_pass  unix:/var/run/php5-fpm.sock;
                fastcgi_pass  unix:/run/php/php7.0-fpm.sock;
                #fastcgi_pass 127.0.0.1:9000;
                # With php5-fpm:
                #fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_index index.php;
                include fastcgi_params;
                fastcgi_buffers 32 32k;
                fastcgi_buffer_size 32k;
                fastcgi_param PATH_INFO       $fastcgi_path_info;
                fastcgi_param PATH_TRANSLATED $document_root$fastcgi_path_info;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name
;
        }

        location ~* ^/(css|img|js|flv|swf|download)/(.+)$ {
                root $root_path;
        }

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        location ~ /\.ht {
                deny all;
        }
}
```
