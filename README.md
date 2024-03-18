## Config
```nginx
user  nobody;
worker_processes  1;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  1024;
}


http {
    server {
        listen       8001;
        server_name  localhost;

        location / {
            proxy_pass http://cip.cc:80;
        }
    }
}
stream {
    server {
        listen 0.0.0.0:22346;
        pass 127.0.0.1:8001;
    }
}

```