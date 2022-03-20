---
layout: post
title: Algoritma Mega Sort
date: 2015-11-07 16:11:00-0400
inline: false
---

***
`Mega sort` merupakan algoritma pengurutan dalam [Ilmu Komputer](https://id.wikipedia.org/wiki/Ilmu_komputer) yang di rancang untuk memenuhi kebutuhan pengurutan atas suatu rangkaian data yang tidak memungkinkan untuk di tampung dalam memory komputer karena jumlahnya terlalu besar. Alogitma ini ditemukan oleh [Jhon Von Neumann](https://id.wikipedia.org/wiki/Arsitektur_von_Neumann#:~:text=John%20Van%20Neumann%20seorang%20ahli,Inggris%3A%20stored%20program%20concept) pada tahun 1945. <br> <br>
[Mega sort](/assets/img/Merge-sort-example-300px.gif)





```python
#Fungsi berikut mengurutkan bilangan pada list menggunakan algoritma merge sort

def merge_sort(list_bilangan):
  jumlah_bilangan =  len(list_bilangan)
  if jumlah_bilangan > 1:
    posisi_tengah = len(list_bilangan)//2
    potongan_kiri = list_bilangan[:posisi_tengah]
    potongan_kanan = list_bilangan[posisi_tengah:]
    
    merge_sort(potongan_kiri)
    merge_sort(potongan_kanan)

    jumlah_bilangan_kiri = len(potongan_kiri)
    jumlah_bilangan_kanan = len(potongan_kanan)
    c_all,c_kiri,c_kanan = 0,0,0 # pencacah/counter
    print('Sebelum merge:',list_bilangan)  
    print('Potongan sebelum merge:',potongan_kiri,':',potongan_kanan)
    while c_kiri < jumlah_bilangan_kiri or c_kanan < jumlah_bilangan_kanan:
      if c_kiri == jumlah_bilangan_kiri: # elemen di potongan kiri habis
        list_bilangan[c_all] = potongan_kanan[c_kanan]
        c_kanan = c_kanan + 1
      elif c_kanan == jumlah_bilangan_kanan: # elemen di potongan kanan habis
        list_bilangan[c_all] = potongan_kiri[c_kiri]
        c_kiri = c_kiri + 1
      elif potongan_kiri[c_kiri] <= potongan_kanan[c_kanan]: # nilai elemen di potongan kiri lebih kecil
        list_bilangan[c_all] = potongan_kiri[c_kiri]
        c_kiri = c_kiri + 1
      else: # nilai elemen di potongan kanan lebih besar
        list_bilangan[c_all] = potongan_kanan[c_kanan]
        c_kanan = c_kanan + 1
      c_all = c_all + 1
    print('Setelah merge:', list_bilangan)
    print()
          
angka = [6,5,3,1,8,7,2,4]
print('Sebelum sort:',angka)
merge_sort(angka)
print('Setelah sort:',angka)
```