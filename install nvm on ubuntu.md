# 1. Hapus Instalasi Node.js dan npm (Opsional)
```
sudo apt remove nodejs npm
```

# 2. Instal NVM
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```
or wget:
```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```

# 3. Muat NVM ke Shell
Setelah instalasi selesai, kamu perlu memuat NVM ke shell. Tambahkan baris berikut ke file konfigurasi shell kamu (~/.bashrc, ~/.bash_profile, atau ~/.zshrc, tergantung pada shell yang kamu gunakan):
```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

# 4. Kemudian, jalankan perintah berikut untuk memuat perubahan:
```
source ~/.bashrc
```
or zsh:
```
source ~/.zshrc
```

# 5. Instal Node.js dengan NVM
```
nvm install --lts
```
or spesifik
```
nvm install 16.19.0
```

# 6. Menggunakan Versi Node.js
```
nvm use --lts
```
Atau untuk versi spesifik:
```
nvm use 16.19.0
```
