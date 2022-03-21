---
layout: post
title: Algoritma KMP Knuth-Morris-Pratt
date:  2022-03-20 07:59:00-0400
redirect: 
inline: false
---

***
`Algoritma KMP (Knuth-Morris-Pratt)` adalah alogritma pencarian string, dikembangkan secara terpisah oleh [`Donald E. Khuth`](https://id.wikipedia.org/wiki/Donald_Knuth) pada tahun 1967 dan `James H. Morris` bersama `Vaughan R. Pratt` pada tahun 1966, tetapi keduanya mempublikasikanya secara bersamaan pada tahun 1977. Jika melihat [Algoritma Brute force](announcement_1.md) lebih mendalam, kita tau bawha dengan mengingat beberapa perbandingan yang dilakukan sebelumnya kita dapat meningkatkan besar pergeseran yang dilakukan. Hal ini akan menghemata perbandingan, yang selanjutnya akan meningkatkan kecepatan pencarian.

***
##### Cara kerja
Perhitungan penggeseran pada algoritma ini adalah sebagai berikut, bila terjadi ketidakcocokan pada saat pattern sejajar `[i..i + n - 1]`, kita bisa menganggap ketidakcocokan pertama terjadi diantara teks `[i + j]` dan pattern `[j]` dengan `0 < j < n`. Berarti, teks `[i..i + n - 1]` = pattern `[0.. j - 1]` dan a = teks `[ i + j]` tidak sama dengan b = pattern `[j]`. Ketika kita menggeser, sangat beralasan bila ada awalan sebuah `v` dari pattern yang akan sama sebagian akhiran `u` dari sebagian teks. Sehingga kita bisa menggeser pattern agar awalan `v` tersebut sejajar dengan akhiran `u`.<br> <br>
Dengan kata lain, pencocokan string akan berjalan secara efisien bila kita mempunyai table yang menentukan berapa panjang kita seharusnya menggeser seandainya terdeteksi ketidakcocokan di karakter `ke-j` dari pattern. Table itu harus memuat `teks[j]` yang merupakan posisi karakter `pattern[j]` setelah digeser, sehingga kita bisa menggeser pattern sebesar `j-next[j]` relatif tehadap teks secara sistematis.<br> 
Langkah-langkah yang dilakukan algoritma `Knuth-Morris-Pratt` pada saat pencocokan string:
* `Algorima Knuth-Morris-Pratt` mulai mencocokan pattern pada awal teks.
* Dari kiri ke kanan, algoritma ini mencocokan karakter per karakter pattern dengan karakter di teks yang bersesuaian, sampai salah satu kondisi berikut terpenuhi:
  * karakter di pattern dan di teks yang di bandingkan tidak cocok (mismatch).
  * semua karakter di pattern cocok, kemudian algoritam akan memberitahukan penemuan di posisi ini.
* Alogtima kemudian menggeser pattern berdasarkan table next, lalu mengulangi langkah kedua sampai berada di ujung teks 

***
##### Syntax KMP
Berikut adalah pseudocode algoritme KMP pada fase pra-pencarian:
```python
rocedure preKMP(
    input P: array[0..n-1] of char,
    input n: integer,
    input/output kmpNext: array[0..n] of integer
)
Deklarasi:
i,j: integer

Algoritme
  i:= 0;
  j:= kmpNext[0]:= -1;
  while (i < n) {
     while (j > -1 and not(P[i] = P[j]))
        j:= kmpNext[j];
     i:= i+1;
     j:= j+1;
     if (P[i] = P[j])
        kmpNext[i]:= kmpNext[j];
     else
        kmpNext[i]:= j;
     endif
  endwhile
```
Dan berikut adalah pseudocode algoritme KMP pada fase pencarian:
```python
procedure KMPSearch(
    input m, n: integer,
    input P: array[0..n-1] of char,
    input T: array[0..m-1] of char,
    output ketemu: array[0..m-1] of boolean
)

Deklarasi:
i, j,next: integer 
kmpNext: array[0..n] of interger

Algoritme:
preKMP(n, P, kmpNext) 
i:=0
while (i<= m-n) do
    j:=0
    while (j < n and T[i+j] = P[j]) do 
       j:=j+1
    endwhile
    if(j >= n) then
       ketemu[i]:=true;
    endif
    next:= j - kmpNext[j]
    i:= i+next
endwhile
```