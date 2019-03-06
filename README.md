# FluxBB

<h1 align="center"><img src="http://fluxbb.org/files/images/logo_large.png" alt="Logo" width="300"/></h1>

## Table of Content
- [Sekilas Tentang](#sekilas-tentang)
- [Instalasi](#instalasi)
  - [Kebutuhan Sistem](#kebutuhan-sistem)
  - [Langkah Instalasi](#langkah-instalasi)
- [Konfigurasi](#konfigurasi)
  - [Styles](#styles)
  - [Language Packs](#language-packs)
  - [Plugins](#plugins)
- [Maintenance](#maintenance)
- [Otomasisasi](#otomasisasi)
- [Cara Pemakaian](#cara-pemakaian)
- [Pembahasan](#pembahasan)
- [Referensi](#referensi)

## Sekilas Tentang

**FluxBB** adalah aplikasi forum *open-source* yang dirilis dibawah GNU General Public Licence dan dapat diunduh dengan gratis. **FluxBB** dirancang sebagai alternatif yang lebih ringan dan cepat untuk beberapa aplikasi forum tradisional yang berat dengan mengurangi fitur-fitur yang "tidak terlalu penting" namun tetap memiliki fitur-fitur yang esensial untuk sebuah aplikasi forum. **FluxBB** mudah digunakan dan sudah memiliki *track record* yang baik untuk kestabilan dan keamanan sehingga bisa menjadi pilihan aplikasi forum yang ideal untuk website Anda.

## Instalasi

### Kebutuhan Sistem
- Sebuah *webserver*
- PHP 5.6.4 atau yang lebih baru
- Sebuah *database*, bisa menggunakan 
  - MySQL 5.0.6 atau yang lebih baru,
  - PostgreSQL 7.0 atau yang lebih baru, atau 
  - SQLite 2

### Langkah Instalasi
Sebelum meng-*install*, [buat VM](https://github.com/auriza/komdat-lab/blob/master/p01.md#membuat-vm-ubuntu-server) yang akan digunakan sebagai *server* dan lakukan [*setting port-forwarding*](https://github.com/auriza/komdat-lab/blob/master/p01.md#setting-port-forwarding-vm) untuk VM tersebut.

1. *Login* ke *server* dengan menggunakan `ssh`, pengguna Windows dapat menggunakan aplikasi [PuTTY](http://www.putty.org/) sebagai alternatif.
  ```
  ssh $(whoami)@localhost -p 2222
  ```

2. Pastikan sistem di *server* sudah *up-to-date*.
  ```
  sudo apt update
  sudo apt upgrade
  ```
  
3. *Install* kebutuhan sistem, sebagai contoh di sini kita menggunakan **Apache** untuk *webserver* dan **MySQL** untuk *database*.
  ```
  sudo apt install apache2 php mysql-server
  sudo apt install php-mysql php-gd php-mbstring php-xml php-curl
  sudo service apache2 restart
  ```

4. Setelah kebutuhan sistem sudah ter-*install*, kita buat *database* beserta *user* untuk aplikasi.
  ```
  sudo mysql -u root -ve "
    CREATE DATABASE fluxbb;
    CREATE USER fluxadmin IDENTIFIED BY 'inipaswort';
    GRANT ALL PRIVILEGES ON fluxbb.* TO fluxadmin;"
  ```
  
5. Unduh berkas instalasi **FluxBB** ke komputer kita. Di sini kita gunakan versi yang *stable* yaitu versi `1.5.11`.
  ```
  wget "https://fluxbb.org/download/releases/1.5.11/fluxbb-1.5.11.tar.gz"
  ```
 
6. Ekstrak berkas yang sudah kita unduh tadi.
  ```
  tar -xvzf fluxbb-1.5.11.tar.gz -C .
  ```
 
7. Pindahkan berkas yang sudah diekstrak tadi ke direktori *webroot*.
  ```
  sudo mv fluxbb-1.5.11 /var/www/html/fluxbb
  ```

8. Ubah otorisasi kepemilikan ke *user* `www-data` (*webserver*).
  ```
  sudo chown -R www-data:www-data /var/www/html/fluxbb
  ```

9. Buka laman <http://localhost:8888/fluxbb> untuk melanjutkan proses instalasi **FluxBB**.
  -
  
  
10. Terakhir kita hapus file instalasi untuk alasan keamanan.
  ```
  sudo rm -rf /var/www/html/fluxbb/install.php
  ```

## Konfigurasi

Untuk meningkatkan kinerja aplikasi, kita dapat melakukan hal-hal berikut seperti yang tercantum di [laman pengembangan **FluxBB**](https://github.com/fluxbb/fluxbb#recommendations).
- Gunakan PHP *accelerator* seperti **APC** atau **XCache** untuk mempercepat waktu eksekusi kode `PHP`.
- Pastikan PHP sudah ter-*install* modul **zlib** agar **FluxBB** dapat membuat output `gzip`.

Ada beberapa modifikasi yang dapat ditambahkan untuk **FluxBB**, yaitu [**Styles**](#styles), [**Language Packs**](#language-packs), dan [**Plugins**](#plugins).
### Styles
**Styles** berfungsi untuk mengubah tampilan atau tema pada aplikasi forum kita, *package-package* untuk modifikasi **Styles** ini dapat diunduh dari [laman *repository* **FluxBB**](http://fluxbb.org/resources/styles/).

Untuk meng-*install*

### Language Packs
**Language Packs** berfungsi untuk menambah opsi bahasa yang bisa digunakan pada aplikasi forum kita, **Language Packs** dapat diunduh dari [laman *repository* **FluxBB**](http://fluxbb.org/resources/translations/).

### Plugins
**Plugins** di **FluxBB** hanya bisa menambahkan fitur untuk *administrator* (dan *moderator* untuk beberapa **Plugins**) saja, **Plugins** berguna untuk menyederhanakan *task administrator* atau menambah fitur yang tidak bisa disediakan oleh **FluxBB** (karena filosofinya). **Plugins** dapat diunduh dari [laman *repository* **FluxBB**](https://github.com/fluxbb/plugins) atau bisa juga kita buat sendiri, *template*-nya dapat diakses di [laman *website* **FluxBB**](https://fluxbb.org/docs/v1.5/plugins). **Plugins** yang dapat digunakan oleh *administrator* diawali dengan `AP`, sedangkan yang dapat digunakan oleh *administrator* dan *moderator* diawali dengan `AMP`.


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

**FluxBB** ditulis dalam bahasa pemrograman `PHP` yang dinamis, cepat, serta didukung oleh banyak *database* dan *web server*. 
Kelebihan aplikasi forum ini antara lain:
- Instalasi dan *setting* yang mudah.
- Ringan dan cepat namun tetap memiliki fitur-fitur yang esensial untuk sebuah aplikasi forum.
- Gratis dan *open-source*, termasuk modifikasi-modifikasinya.
- Antarmuka yang *clean* dan mudah dipahami.
- *Permission system* yang fleksibel.
- *Moderator tools* yang lengkap dan *powerful*.
- Banyak modifikasi yang tersedia dari *community*-nya.

Selain memiliki kelebihan, aplikasi ini juga punya kekurangan, antara lain:
- Fitur-fitur yang tersedia hanya yang "standar" saja.
- Tampilan antarmuka yang terkesan *plain* dan kurang menarik.
- Modifikasi **Plugins** yang bisa dibuat hanya sebatas untuk *administrator* dan *moderator* saja.
- Tidak ada fitur *private message*, tetapi menyediakan *e-mail form*.
- Secara default tidak mendukung fitur *attachment* dan *third party login*, tetapi ada **Plugins** yang dapat di-*install* untuk menambah fitur tersebut.

Contoh aplikasi forum lainnya adalah **Discourse**, aplikasi ini ditulis dalam bahasa `Ruby` dan `JavaScript`. Jika dibandingkan dengan **FluxBB**, masing-masing memiliki kelebihan dan kekurangan an1tara lain:
- **Discourse** secara default memiliki fitur yang lebih banyak dibanding **FluxBB**.
- *Plugin-plugin* yang tersedia di **Discourse** lebih banyak dibanding **FluxBB**.
- Tampilan antarmuka **Discourse** lebih menarik dibanding **FluxBB**.
- **Discourse** tidak sepenuhnya gratis, untuk sebagian fitur seperti *storage space*, jumlah staf (*administrator*, *moderator*), dan *plugin* yang dapat digunakan secara gratis terbatas jumlahnya. Sedangkan **FluxBB** sepenuhnya gratis.
- **FluxBB** lebih ringan dan cepat dari **Discourse**.
- Instalasi **FluxBB** lebih mudah karena berbasis bahasa `PHP`, instalasi **Discourse** lebih rumit dan memerlukan lebih banyak *requirements* karena berbasis `Ruby` dan `JS`.

## Referensi

1. [FluxBB Website](https://fluxbb.org/) - FluxBB
2. [FluxBB Development Repository](https://github.com/fluxbb/fluxbb) - FluxBB GitHub
3. [Panduan Pembuatan VM dan *Setting Port-forwarding*](https://github.com/auriza/komdat-lab/blob/master/p01.md) - GitHub Pak Auriza
