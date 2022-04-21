
[VueJs](#vuejs)


## Vue Js 

`root` folder project for example : `/var/www/html/project/dist`

```
server {
    listen       80;
    server_name  localhost;
    location / {
      root   /var/www/html/project/dist;
      index  index.html;
      try_files $uri $uri/ /index.html;
    }
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
      root   /usr/share/nginx/html;
    }
}
```
