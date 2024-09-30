# Fail2Ban untuk Melindungi dari Serangan Brute Force
  - Fail2Ban adalah tool yang memblokir IP yang mencoba login terlalu sering dengan salah. Instal Fail2Ban:
    ```
    sudo apt install fail2ban
    ```
  - Aktifkan dan konfigurasi jails default untuk melindungi layanan seperti SSH:
    ```
    sudo systemctl enable fail2ban
    sudo systemctl start fail2ban
    ```

# Amankan Layanan dan Aplikasi
  - Pastikan hanya layanan dan aplikasi yang diperlukan saja yang berjalan. Nonaktifkan layanan yang tidak digunakan. Daftar layanan yang berjalan:
    ```
    sudo systemctl list-units --type=service
    ```

# Konfigurasi SSH pada Port yang Berbeda
  - Mengubah port default SSH (22) dapat membantu mengurangi jumlah serangan brute force otomatis. Edit file konfigurasi SSH:
    ```
    sudo nano /etc/ssh/sshd_config
    ```
  - Ubah port ke nomor lain (misalnya 2200):
    ```
    Port 2200
    ```
  - Jangan lupa untuk mengizinkan port baru di firewall:
    ```
    sudo ufw allow 2200/tcp
    ```

# Audit Keamanan dengan Lynis
  - Lynis adalah alat audit keamanan yang dapat digunakan untuk memeriksa celah keamanan pada sistem. Instal Lynis dan jalankan audit:
    ```
    sudo apt install lynis
    sudo lynis audit system
    ```
