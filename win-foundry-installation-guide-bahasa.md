# Instalasi Foundry di Windows

Panduan ini merupakan metode untuk menginstal Foundry di Windows, menggunakan WSL (Windows Subsystem for Linux).

## Prasyarat

Sebelum menginstal Foundry, pastikan memiliki:

- Windows 10 versi 2004 dan lebih tinggi (Build 19041 dan lebih tinggi) atau Windows 11
- Akses admin ke komputer
- Setidaknya 5GB ruang disk kosong
- Emulator terminal (Windows Terminal direkomendasikan)

### Langkah 1: Instal WSL

1. Buka PowerShell atau Command Prompt Windows sebagai Administrator
2. Jalankan perintah berikut:

```powershell
wsl --install
```

Command ini akan otomatis menginstal Ubuntu. Jika ingin menggunakan versi tertentu, gunakan:

```powershell
wsl --install -d Ubuntu-22.04
```

3. Restart komputer ketika diminta
4. Setelah restart, terminal akan terbuka secara otomatis untuk menyelesaikan pengaturan Ubuntu
5. Buat nama pengguna dan kata sandi ketika diminta

### Langkah 2: Instal Foundry di WSL

1. Buka terminal WSL (Ubuntu)
2. Jalankan perintah berikut untuk menginstal Foundryup:

```bash
curl -L https://foundry.paradigm.xyz | bash
```

3. Ikuti petunjuk untuk menyelesaikan instalasi
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

### Langkah 3: Instal VS Code dan Ekstensi Remote Development

Buka VS Code dan instal ekstensi "Remote Development" dari Microsoft jika belum menginstalnya.

### Langkah 4: Hubungkan VS Code ke WSL

1. Klik tombol di pojok kiri bawah VS Code
2. Pilih "Connect to WSL" dari menu dropdown
3. VS Code akan dibuka kembali terhubung ke environment WSL

### Langkah 5: Siapkan Node.js di WSL

Buka terminal VS Code yang telah terhubung ke WSL dan instal nvm dan Node.js:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# Source nvm
source ~/.bashrc # atau source ~/.zshrc jika Anda menggunakan zsh
# Instal dan gunakan Node.js 18
nvm install 18
nvm use 18
```

### Langkah 6: Instal Yarn

Instal package manager Yarn (Kita membutuhkan yarn sebagai package manager untuk workshop ini):

```bash
npm install -g yarn
```

### Langkah 7: Mengkloning Repositori

Setelah semua disiapkan, kita dapat mengkloning repositori yang terkait dengan workshop ini nanti.

## Permasalahan Umum Instalasi

### Masalah Umum

1. **Error "Command not found":**

   - Pastikan telah membuka sesi terminal baru setelah instalasi
   - Periksa bahwa binari ada di PATH

2. **Masalah izin:**

   - Di WSL, mungkin perlu menggunakan `sudo` untuk beberapa operasi
   - Di Windows, jalankan terminal sebagai Administrator

3. **Error otentikasi Git:**

   - Atur kredensial Git pada terminal dengan:
     ```bash
     git config --global user.email "email-anda@example.com"
     git config --global user.name "Nama Anda"
     ```

4. **Masalah integrasi WSL:**
   - Pastikan mengakses file Windows dengan benar melalui jalur `/mnt/c/` di WSL
   - Pertimbangkan untuk menggunakan VSCode dengan ekstensi "Remote - WSL" untuk pengembangan yang mulus

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
