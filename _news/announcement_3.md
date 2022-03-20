---
layout: post
title: Membalikan urutan string
date: 2022-03-20 07:59:00-0400
inline: false
---

<b>Kasus</b> anggap saja anda ingin membalikan urutan string, misalnya `Python` menjadi `nothyP`

***
<b>Solusi</b> untuk menangani permasalahan seperti di atas, kita bisa membuat fungsi sendiri menggunakan code berikut
```python
def reverseString(s):
    1str = list(s)
    i=0; j=len(s)-1
    while (i < j):
        temp = 1str[i]
        1str[i] = 1str[j]
        1str[j] = temp
        i += 1; j -= 1
        i += 1; j -= 1
    return ''. join(1str)

reverseString(Python)
```
***