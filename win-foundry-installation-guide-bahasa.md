# Instalasi Foundry

Panduan ini adalah metode untuk menginstal Foundry pada sistem macOS dan Windows.

## Instalasi Foundry di macOS

Instalasi di macOS cukup sederhana karena sudah dilengkapi dengan lingkungan berbasis Unix.

### Prasyarat

Sebelum menginstal Foundry di macOS, pastikan memiliki:
- macOS 10.15 Catalina atau lebih baru
- Aplikasi Terminal
- Setidaknya 1GB ruang disk kosong

### Langkah-langkah Instalasi macOS

1. Buka Terminal
2. Jalankan skrip instalasi Foundryup:
   ```bash
   curl -L https://foundry.paradigm.xyz | bash
   ```
3. Instal package libusb apabila belum terinstal
   ```bash
   brew install libusb
   ```
4. Mulai sesi terminal baru atau jalankan:
   ```bash
   source ~/.zshrc  # atau source ~/.bash_profile tergantung shell
   ```
5. Instal Foundry dengan menjalankan:
   ```bash
   foundryup
   ```
6. Verifikasi instalasi dengan memeriksa versi:
   ```bash
   forge --version
   cast --version
   anvil --version
   ```

**Setelah menyelesaikan instalasi macOS, lanjutkan ke bagian [Pengaturan Node.js](#pengaturan-nodejs).**

## Instalasi Foundry di Windows

Instalasi Windows memerlukan WSL (Windows Subsystem for Linux) untuk menyediakan lingkungan Linux.

### Prasyarat untuk Windows

Sebelum menginstal Foundry di Windows, pastikan memiliki:
- Windows 10 versi 2004 dan lebih tinggi (Build 19041 dan lebih tinggi) atau Windows 11
- Akses admin ke komputer
- Setidaknya 5GB ruang disk kosong
- Emulator terminal (Windows Terminal direkomendasikan)

### Langkah 1: Aktifkan Fitur Hyper-V

1. Tekan tombol Windows dan cari "Turn Windows features on or off" ("Aktifkan atau nonaktifkan fitur Windows")
2. Pada dialog Windows Features, scroll ke bawah dan centang kotak di samping "Hyper-V"
3. Klik OK dan tunggu hingga fitur tersebut diinstal
5. Restart komputer ketika diminta

### Langkah 2: Instal WSL

1. Buka PowerShell atau Command Prompt Windows sebagai Administrator
2. Jalankan perintah berikut:
   ```powershell
   wsl --install
   ```
   Command ini akan otomatis menginstal Ubuntu. Jika ingin menggunakan versi tertentu, gunakan:
   ```powershell
   wsl --install -d Ubuntu-22.04
   ```
3. Restart komputer untuk sepenuhnya mengaktifkan fitur yang telah terinstal.

### Langkah 3: Instal Foundry di WSL

1. Buka terminal WSL (Ubuntu)
2. Buat nama unix pengguna dan kata sandi ketika diminta
3. Setelah dibuat, jalankan perintah berikut untuk menginstal Foundryup:
   ```bash
   curl -L https://foundry.paradigm.xyz | bash
   ```
4. Mulai sesi terminal baru atau pada terminal yang sama, dan jalankan:
   ```bash
   source ~/.bashrc
   ```
5. Instal Foundry dengan menjalankan:
   ```bash
   foundryup
   ```
6. Verifikasi instalasi dengan memeriksa versi:
   ```bash
   forge --version
   cast --version
   anvil --version
   ```

### Langkah 4: Instal VS Code dan Ekstensi Remote Development

Buka VS Code dan instal ekstensi "Remote Development" dari Microsoft jika belum menginstalnya.

### Langkah 5: Hubungkan VS Code ke WSL

1. Klik tombol di pojok kiri bawah VS Code
2. Pilih "Connect to WSL" dari menu dropdown
3. VS Code akan dibuka kembali terhubung ke environment WSL

## Pengaturan Node.js

<a name="pengaturan-nodejs"></a>

### Untuk macOS

Buka Terminal dan jalankan command 

```bash
node -v 
```

Apabila tidak ditemukan, maka instal nvm dan Node.js:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# Source nvm
source ~/.zshrc  # atau source ~/.bash_profile tergantung shell
# Instal dan gunakan Node.js 18
nvm install 18
nvm use 18
```

### Untuk Windows (WSL)

Buka terminal VS Code yang telah terhubung ke WSL dan instal nvm dan Node.js:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# Source nvm
source ~/.bashrc
# Instal dan gunakan Node.js 18
nvm install 18
nvm use 18
```

## Instalasi Yarn

Instal package manager Yarn (dibutuhkan sebagai package manager untuk workshop ini):

```bash
npm install -g yarn
```

## Mengkloning Repositori

Setelah semua disiapkan, kita dapat mengkloning repositori yang terkait dengan workshop ini nanti.

## Permasalahan Umum

### Masalah Umum di Windows

1. **Hyper-V tidak tersedia:**
   - Pastikan virtualisasi diaktifkan dalam pengaturan BIOS/UEFI komputer
   - Verifikasi bahwa edisi Windows mendukung Hyper-V (Pro, Enterprise, atau Education)
   - Jalankan `systeminfo` di Command Prompt untuk memeriksa apakah virtualisasi diaktifkan

2. **Error "Command not found":**
   - Pastikan telah membuka sesi terminal baru setelah instalasi
   - Periksa bahwa binari ada di PATH

3. **Masalah izin:**
   - Di WSL, mungkin perlu menggunakan `sudo` untuk beberapa operasi
   - Di Windows, jalankan terminal sebagai Administrator

4. **Error otentikasi Git:**
   - Atur kredensial Git pada terminal dengan:
     ```bash
     git config --global user.email "email-anda@example.com"
     git config --global user.name "Nama Anda"
     ```

5. **Masalah integrasi WSL:**
   - Pastikan mengakses file Windows dengan benar melalui jalur `/mnt/c/` di WSL
   - Pertimbangkan untuk menggunakan VSCode dengan ekstensi "Remote - WSL" untuk pengembangan yang mulus

### Masalah Umum di macOS

1. **Error izin:**
   - Mungkin perlu menggunakan `sudo` untuk beberapa operasi
   - Pastikan memiliki izin yang benar

2. **Command not found setelah instalasi:**
   - Pastikan profil shell (`.zshrc` atau `.bash_profile`) telah diperbarui dan di-source
   - Periksa bahwa binari Foundry ada di PATH

3. **Error tidak ditemukan instalasi 

## Memulai dengan Foundry

Setelah instalasi, coba buat proyek pertama:
```bash
# Buat direktori baru
mkdir hello-foundry
cd hello-foundry
# Inisialisasi proyek Foundry baru
forge init
```

Jalankan tes:
```bash
forge test
```

Untuk informasi lebih lanjut atau instalasi alternatif, periksa [Foundry Book](https://book.getfoundry.sh/).
