# Setting Puppeter
```
puppeteer: {
    headless: true, // Browser berjalan tanpa UI
    args: [
      '--no-sandbox',                // Nonaktifkan sandbox, wajib untuk VPS/Docker tanpa GUI
      '--disable-setuid-sandbox',   // Nonaktifkan setuid sandbox
      '--disable-dev-shm-usage',    // Gunakan shared memory yang lebih kecil (jika perlu)
      '--disable-accelerated-2d-canvas',
      '--no-zygote',
      '--single-process',           // Opsi opsional untuk stabilitas proses Chromium
      '--disable-gpu'               // Nonaktifkan GPU (biasanya headless)
    ],
  },
```

# Install library
```
sudo apt install -y \
  gconf-service \
  libasound2 \
  libatk1.0-0 \
  libc6 \
  libcairo2 \
  libcups2 \
  libdbus-1-3 \
  libexpat1 \
  libfontconfig1 \
  libgcc1 \
  libgconf-2-4 \
  libgdk-pixbuf2.0-0 \
  libglib2.0-0 \
  libgtk-3-0 \
  libnspr4 \
  libnss3 \
  libpango-1.0-0 \
  libx11-6 \
  libx11-xcb1 \
  libxcb1 \
  libxcomposite1 \
  libxcursor1 \
  libxdamage1 \
  libxext6 \
  libxfixes3 \
  libxi6 \
  libxrandr2 \
  libxrender1 \
  libxss1 \
  libgbm-dev \
  libxtst6 \
  ca-certificates \
  fonts-liberation \
  libappindicator1 \
  libnss3 \
  lsb-release \
  xdg-utils \
  libgbm-dev \
  libxss1 \
  libasound2 \
  libatk1.0-0 \
  libcups2 \
  libx11-xcb1 \
  libxcomposite1 \
  libxrandr2 \
  libxrender1 \
  libxi6 \
  libxtst6 \
  libnss3 \
  fonts-liberation \
  libappindicator1 \
  libgtk-3-0 \
  wget
```
