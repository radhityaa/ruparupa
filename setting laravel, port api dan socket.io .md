# setting 1 project dengan laravel, nodejs, express dan websocket (socket.io)

## settingan nginx
```
location /socket.io/ {
    proxy_pass http://127.0.0.1:5000; # arahkan ke server Socket.IO
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}
```

```
location /api/ {
        proxy_pass http://127.0.0.1:4000; # Port API Express
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```

pastikan URL WS (websocket) hanya domain saja ex: https://ayasyatech.com
