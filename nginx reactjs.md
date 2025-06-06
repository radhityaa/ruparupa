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
#Jika sudah pasang SSL HTTPS Certbot
jika error duplicate coba saja hapus location / yang pertama atau ke dua (harus satu)
```
server {
    listen 80;
    server_name www.privateclass.tofaapps.com privateclass.tofaapps.com;

    location / {
        root /var/www/privateclass.tofaapps.com;
        try_files $uri /index.html;
        index index.html;
    }

    # Redirect HTTP to HTTPS
    location / {
        return 301 https://$server_name$request_uri;
    }
}

server {
    listen 443 ssl;
    server_name www.privateclass.tofaapps.com privateclass.tofaapps.com;

    ssl_certificate /etc/letsencrypt/live/privateclass.tofaapps.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/privateclass.tofaapps.com/privkey.pem;

    location / {
        root /var/www/privateclass.tofaapps.com;
        try_files $uri /index.html;
        index index.html;
    }
}
```
