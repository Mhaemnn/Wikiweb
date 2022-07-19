---
layout: post
title:  Installasi Katoolin
date:   2022-02-10 16:40:16
description: 
tags: formatting links
categories: Python

---
***
## Installasi Katoolin
Katoolin adalah sebuah tools yang dibangun menggunakan bahasa pemrograman ptyhon, difungsikan untuk untuk menginstalasi dan menggunakan tools-tools yang ada di kali linux.

### Installasi katoolin di Ubuntu 20.04 LTS
Saya telah menguji katoolin3 di edisi server ubuntu 20.04 LTS. Namun, ini harus bekerja pada versi dan turunanya ubuntu lainya. 
Katoolin memerlukan persyaratan berikut di sistem ubuntu:
<ul>
<li>Python >= 3.5</li>
<li>Git</li>
<li>sh.bash</li>
<li>Python3-apt</li>
</ul>
Tapi biasanya paket-paket ini sudah di install sebelumnya di ubuntu 20.04 LTS terbru, jadi anda tidak perlu menginstal lagi <br>

* dan, pastikan sudah mengaktifkan repositori [unverse] 

```bush
sudo apt-get-repository universe
```
* Kloning repositori katoolin3 Github menggunakan printah

```bush
git clone https://github.com/s-h-3-l-l/katoolin3
```
pastikan nama repositori sudah bener. Di URL di atas, seharusnya dua huruf kecil "L" dalam kata "s-h-3-l-l"

* Masukan ke diroktori katoolin
```bush
cd katoolin3
```

* Jadikan install.sh dapat di ekeksekusi
```bush
chmod +x ./isntall.sh
```
* Kemudain install katoolin3 menggunakan printah
```bush
sudo ./install.sh
```
* jalan katoolin
```bush
sudo katoolin / katoolin
```


## Untuk mengatasi Error jika terjadi 1
```bush
Executing: /tmp/apt-key-gpghome.djOjFHnxMn/gpg.1.sh -qq --keyserver pool.sks-keyservers.net --recv-keys ED444FF07D8D0BF6
gpg: keyserver receive failed: Server indicated a failure
Executing: /tmp/apt-key-gpghome.y9Tms4BOS4/gpg.1.sh -qq --keyserver hkp://pool.sks-keyservers.net:80 --recv-keys ED444FF07D8D0BF6
gpg: keyserver receive failed: Server indicated a failure
This may be a server issue. Please try again later

```
Server kunci SKS tidak digunakan lagi dan sebagian besar offline. Dengan demikian anda tidak dapat mengambil kunci dari mereka sebagai gantinya bisa menggunakan perintah di bawah ini
buka install.sh menggunakan teks editor kesayangan anda,
dan fastekan kode berikut ini:

```bush
nano install.sh
 apt-key adv -qq --keyserver keyserver.ubuntu.com --recv-keys ED444FF07D8D0BF6 || apt-key adv -qq --keyserver hkp://keyservers.ubuntu.com:80 --recv-keys ED444FF07D8D0BF6 || die "This may be a server issue. Please try again later"
```
Setelah itu jalan kan lagi `chmod +x ./install.sh && sudo ./install.sh`
## Untuk mengatasi Error jika terjadi 2
```bush
please install the 'python3-apt' package
```
Silahkan coba menginstall ulang dan paket ini dari paket 
```bush
sudo apt-get update && apt-get install --reinstall ptyhon3-apt
```