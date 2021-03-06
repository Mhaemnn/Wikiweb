---
layout: post
title: Algoritma Merge Sort Python
date:  2020-03-11 16:40:00-0900
inline: false
---

***
##### Pengertian
`Mega sort` merupakan algoritma pengurutan dalam [Ilmu Komputer](https://id.wikipedia.org/wiki/Ilmu_komputer) yang di rancang untuk memenuhi kebutuhan pengurutan atas suatu rangkaian data yang tidak memungkinkan untuk di tampung dalam memory komputer karena jumlahnya terlalu besar. Alogitma ini ditemukan oleh [Jhon Von Neumann](https://id.wikipedia.org/wiki/Arsitektur_von_Neumann#:~:text=John%20Van%20Neumann%20seorang%20ahli,Inggris%3A%20stored%20program%20concept) pada tahun 1945. <br> <br>

##### Algoritma 
Perinsip utama yang diimplementasikan pada algoritma `Merge sort` sering kali disebut sebagai *Divide and Conquer*. Cara kerja algoritam `Merge sort` adalah membagi [larik](https://id.wikipedia.org/wiki/Larik) yang diberikan menjadi dua bagian yang lebih kecil, kedua larik tersebut akan diurutkan secara terpisah. Setelah kedua buah list tersusun, makan akan dibentuk larik baru sebagai hasil penggabungan dari dua buah larik sebelumnya. Menurut keefektifanya, algoritma ini bekarja dengan tingkat keefektifan [O](https://id.wikipedia.org/wiki/Notasi_O_besar)(nlog(n)). Dalam bentuk pseudocode sederhana algoritam ini dijabarkan sebagia berikut:
```python
# Original data is on the input tape; the other tapes are blank
 function merge_sort(input_tape, output_tape, scratch_tape_C, scratch_tape_D)
     while any records remain on the input_tape
         while any records remain on the input_tape
             merge( input_tape, output_tape, scratch_tape_C)
             merge( input_tape, output_tape, scratch_tape_D)
         while any records remain on C or D
             merge( scratch_tape_C, scratch_tape_D, output_tape)
             merge( scratch_tape_C, scratch_tape_D, input_tape)

 # take the next sorted chunk from the input tapes, and merge into the single given output_tape.
 # tapes are scanned linearly.
 # tape[next] gives the record currently under the read head of that tape.
 # tape[current] gives the record previously under the read head of that tape.
 # (Generally both tape[current] and tape[previous] are buffered in RAM ...)
 function merge(left[], right[], output_tape[])
     do
        if left[current] ??? right[current]
            append left[current] to output_tape
            read next record from left tape
        else
            append right[current] to output_tape
            read next record from right tape
    while left[current] < left[next] and right[current] < right[next]
    if left[current] < left[next]
        append current_left_record to output_tape
    if right[current] < right[next]
        append current_right_record to output_tape
    return
```
Contoh penerapan atas sebuah larik sebagai data sumber yang akan diturunkan ***{3,9,4,1,5,2}*** adalah sebagai berikut:
* Larik tersebuh dibagi menjadi dua bagian,***{3,9,4}*** dan ***{1,5,2}***
* Kedua lirik kemudian diurutakan secara terpisah sehingga menjadi ***{3,9,4}*** dan ***{1,5,2}***
* Sebuah lirik baru dibentuk sebagai penggabung dari kedua lirik tersebut ***{1}***, sementara nilai-nilai dalam masing larik ***{3,4,9}*** dan ***{2,5}*** (nilai `1` dalam elemen larik kedua telah dipindahkan ke larik baru)
* Langkah berikutnya adalah penggabungan dari masing-masing larik ke dalam larik baru yang dibuat sebelumnya.
  * ***{1, 2}*** <-> ***{3, 4, 9}*** dan ***{5}***
  * ***{1, 2, 3}*** <-> ***{4, 9}*** dan ***{5}***
  * ***{1, 2, 3, 4}*** <-> ***{9}*** dan ***{5}***
  * ***{1, 2, 3, 4, 5}*** <-> ***{9}*** dan ***{null}***
  * ***{1, 2, 3, 4, 5, 9}*** <-> ***{null}*** dan ***{null}***
