# FluxBB
<center><img src="http://fluxbb.org/files/images/logo_large.png"></center>


## Sekilas Tentang

Deskripsi singkat tentang aplikasi tsb.


## Instalasi

- Prasyarat, apa saja yang harus diinstal sebelumnya.
- Langkah instalasi dalam CLI.
```
ssh student@localhost -p 2222
```

```
sudo apt update
sudo apt upgrade
sudo apt install apache2 php mysql-server
sudo apt install php-mysql php-gd php-mbstring php-xml php-curl
sudo service apache2 restart
```

```
sudo mysql -u root -ve "
  CREATE DATABASE fluxbb;
  CREATE USER fluxadmin IDENTIFIED BY 'inipaswort';
  GRANT ALL PRIVILEGES ON fluxbb.* TO fluxadmin;"
```
  
```
wget "https://fluxbb.org/download/releases/1.5.11/fluxbb-1.5.11.tar.gz"
```
 
```
tar -xvzf fluxbb-1.5.11.tar.gz -C .
```
 
```
sudo mv fluxbb-1.5.11 /var/www/html/fluxbb
```

```
sudo chown -R www-data:www-data /var/www/html/fluxbb
```

```
sudo rm -rf /var/www/html/fluxbb/install.php
```

## Konfigurasi (opsional)

Setting server tambahan yang diperlukan untuk meningkatkan fungsi dan kinerja aplikasi, misalnya:
- batas upload file
- batas memori
- dll

Plugin untuk fungsi tambahan
- login dengan Google/Facebook
- editor Markdown
- dll


##  Maintenance (opsional)

Setting tambahan untuk maintenance secara periodik, misalnya:
- buat backup database tiap pekan
- hapus direktori sampah tiap hari
- dll


## Otomatisasi (opsional)

Skrip shell untuk otomatisasi instalasi, konfigurasi, dan maintenance.


## Cara Pemakaian

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## Pembahasan

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
- Bandingkan dengan aplikasi web lain yang sejenis


## Referensi

Cantumkan tiap sumber informasi yang anda pakai.
