# Panduan Mengatur Kunci SSH untuk GitHub

## 1. Instal Git
```bash
sudo apt update && sudo apt install git -y
```

## 2. Membuat Kunci SSH
```bash
# Pindah ke direktori SSH
cd ~/.ssh/

# Buat kunci SSH baru (RSA)
ssh-keygen -t rsa -b 4096 -C "email_anda@example.com"
```
- Saat diminta:
  - **File penyimpanan kunci**: Tekan Enter (lokasi default `~/.ssh/id_rsa`)
  - **Passphrase (opsional)**: Masukkan atau langsung Enter jika tidak perlu.

## 3. Lihat dan Salin Kunci Publik
```bash
cat ~/.ssh/id_rsa.pub
```
- Salin seluruh hasil yang ditampilkan.

## 4. Tambahkan Kunci SSH ke GitHub
1. Buka **GitHub**: [https://github.com](https://github.com)
2. Masuk ke: **Settings > SSH and GPG keys**
3. Klik **New SSH Key**:
   - **Title**: Nama deskriptif (misalnya, "Laptop Saya")
   - **Key**: Tempelkan kunci publik yang sudah disalin
4. Klik **Add SSH Key**

## 5. Konfigurasi SSH untuk GitHub
```bash
nano ~/.ssh/config
```
- Tambahkan isi berikut:
```ini
Host github.com
  Hostname ssh.github.com
  Port 443
  User git
  IdentityFile ~/.ssh/id_rsa
```
- Simpan dan keluar (`CTRL+X`, lalu `Y`, dan tekan `Enter`).

## 6. Uji Koneksi SSH
```bash
ssh -T git@github.com
```
- Jika berhasil, muncul pesan:
  *"Hi username! You've successfully authenticated, but GitHub does not provide shell access."*

## 7. Atur Identitas Git (Opsional, tetapi Disarankan)
```bash
git config --global user.name "Nama Anda"
git config --global user.email "email_anda@example.com"
```

## 8. Periksa Konfigurasi Git
```bash
git config --list
```

### 🎉 Selesai! Anda kini dapat melakukan clone dan push repository menggunakan SSH tanpa memasukkan kredensial setiap saat.


https://docs.google.com/presentation/d/1zs1nRrFOPHNjIvcjZTV-iAjXeygDJzob/edit#slide=id.p54
