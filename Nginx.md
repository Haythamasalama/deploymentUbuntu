# Nginx Config Servers  

- [VueJs](#vue-js)

## Vue Js 

```
server {
    listen       80;
    server_name  localhost;
    location / {
      root   /srv/example.com/dist;
      index  index.html;
      try_files $uri $uri/ /index.html;
    }
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
      root   /usr/share/nginx/html;
    }
}
```
> [More info](https://cli.vuejs.org/guide/deployment.html#docker-nginx)

