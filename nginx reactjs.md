```
server {
        listen 80;
        listen [::]:80;

        root /var/www/your_domain/html;
        index index.html index.htm index.nginx-debian.html;

        server_name www.your_domain;

        location / {
                try_files $uri $uri/ =404;
        }
}

```
#ATAU
```
server {
    listen 80;
    server_name www.privateclass.tofaapps.com privateclass.tofaapps.com;

    location / {
        root /var/www/privateclass.tofaapps.com;
        try_files $uri /index.html;
        index index.html;
    }
}
```
