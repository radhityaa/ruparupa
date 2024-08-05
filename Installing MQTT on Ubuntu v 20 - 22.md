## 1. Update Sistem
Pastikan sistem diperbarui:

```bash
sudo apt update
```

```
sudo apt upgrade
```

## 2. Instal Mosquitto
Instal Mosquitto dan utilitas kliennya:

```
sudo apt install mosquitto mosquitto-clients
```

## 3. Konfigurasi Mosquitto
Secara default, Mosquitto akan mulai otomatis setelah instalasi. Namun, Anda mungkin ingin mengonfigurasi file mosquitto.conf untuk mengatur pengaturan seperti port, otentikasi, dan lainnya.

* Edit file konfigurasi:

```
sudo nano /etc/mosquitto/mosquitto.conf
```

Anda bisa menambahkan atau mengubah konfigurasi di sini. Misalnya, Anda bisa mengatur port, mengaktifkan otentikasi, atau menetapkan hak akses. Berikut adalah contoh konfigurasi sederhana yang mendengarkan pada port 1883 (port default untuk MQTT):

```
listener 1883
protocol mqtt
```

* Restart Mosquitto setelah melakukan perubahan:

```
sudo systemctl restart mosquitto
```
## 4. Verifikasi Instalasi
* Cek status Mosquitto:

```
sudo systemctl status mosquitto
```

Pastikan layanan berjalan dengan baik.

* Gunakan klien Mosquitto untuk menguji broker:
Buka terminal lain dan uji dengan mosquitto_sub dan mosquitto_pub:

- Berlangganan ke topik:
  ```
  mosquitto_sub -h localhost -t "test/topic"
  ```
  
- Menerbitkan pesan ke topik:
  ```
  mosquitto_pub -h localhost -t "test/topic" -m "Hello MQTT"
  ```
  Jika konfigurasi Anda benar, Anda akan melihat pesan "Hello MQTT" muncul di terminal yang menjalankan mosquitto_sub.

## 5. Mengonfigurasi Firewall (Opsional)
Jika Anda menggunakan firewall seperti ufw, pastikan port 1883 terbuka:
```
sudo ufw allow 1883/tcp
```

## 6. Opsi Otentikasi dan Otorisasi (Opsional)
Untuk menambahkan otentikasi dasar atau mengonfigurasi kontrol akses, Anda bisa mengedit file konfigurasi mosquitto.conf:
```
sudo nano /etc/mosquitto/mosquitto.conf
```

* Menambahkan otentikasi:
  Tambahkan username dan password:
  ```
  allow_anonymous false
  password_file /etc/mosquitto/pwfile
  ```
  Buat file password:
  ```
  sudo mosquitto_passwd -c /etc/mosquitto/pwfile your_username
  ```
  
* Menambahkan kontrol akses:
  Buat file ACL:
  ```
  sudo nano /etc/mosquitto/aclfile
  ```
  
  Contoh konten file ACL:
  ```
  user your_username
  topic readwrite #
  ```

  Update file konfigurasi mosquitto.conf untuk menggunakan ACL:
  ```
  sudo nano /etc/mosquitto/mosquitto.conf
  ```
  ```
  acl_file /etc/mosquitto/aclfile
  ```
  Restart Mosquitto untuk menerapkan perubahan:
  ```
  sudo systemctl restart mosquitto
  ```

  ## 7. Uji Koneksi dengan Klien MQTT
  Gunakan alat seperti mosquitto_pub dan mosquitto_sub untuk menguji koneksi ke broker MQTT dengan kredensial yang sama:

  * Publish Message:
    ```
    mosquitto_pub -h MQTT_BROKER_IP -p 1883 -u "Your_MQTT_USERNAME" -P "Your_MQTT_PASSWORD" -t "test/topic" -m "Hello MQTT"
    ```
    
  * Subscribe to Topic:
    ```
    mosquitto_sub -h MQTT_BROKER_IP -p 1883 -u "Your_MQTT_USERNAME" -P "Your_MQTT_PASSWORD" -t "test/topic"
    ```

  ## 8. Cek Log Mosquitto
  ```
  sudo journalctl -u mosquitto
  ```
