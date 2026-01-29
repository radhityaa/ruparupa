```
# 1. Definisikan grup server (Load Balancer)
upstream websocket_backend {
    # Secara default menggunakan metode Round Robin (bergantian)
    # Tambahkan 'ip_hash;' jika Anda ingin user yang sama selalu connect ke port yang sama (penting untuk WebSocket stateful)
    # ip_hash; 
    
    server localhost:3001;
    server localhost:3002;
    server localhost:3003;
}

server {
    listen 80;
    server_name websocket.test;

    location / {
        # 2. Arahkan proxy_pass ke nama upstream di atas
        proxy_pass http://websocket_backend;

        # Header standar untuk WebSocket
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        
        # Header tambahan agar backend tahu IP asli client
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        # Cache bypass (sesuai config asli Anda)
        proxy_cache_bypass $http_upgrade;
        
        # Opsional: Perpanjang timeout jika WebSocket sering putus
        proxy_read_timeout 300s;
        proxy_send_timeout 300s;
    }
}
```
