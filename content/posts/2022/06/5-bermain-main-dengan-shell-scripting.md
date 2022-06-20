---
title: "Bermain-main dengan Shell Scripting"
date: 2022-06-14T18:26:12+07:00
draft: false
---

```ruby
puts "Sekali mendayung dua tiga pulau terlampaui."
```

# 🥑 Appetizer

Melanjutkan post sebelumnya, di sini gua bakal nge-share sedikit apa itu Shell scripting dan bagaimana cara menggunakannya. Shell scripting bisa digunakan untuk menjalankan beberapa command sekaligus, plus, kita bisa memasukkan logic yang kompleks dengan menggunakan Shell script.

# 🥩 Main Course

### A. Apa itu Shell script?

Mengacu pada halaman Wikipedia [ini](https://en.wikipedia.org/wiki/Shell_script), Shell script adalah sebuah program komputer yang dirancang untuk dijalankan oleh Unix shell, sebuah _command-line interpreter_.

Gua males nulis interpretasi gua sendiri, jadi pake dari Wikipedia di atas aja ya 😅

### B. Cara membuat file Shell script

Kita bisa membuat file Shell script sama seperti membuat file pada umumnya. Ekstensi yang digunakan untuk file Shell script adalah `.sh`.

Untuk _naming convention_-nya sendiri sepertinya bebas/tidak ada aturan strict. Tapi, kalo gua sendiri sih prefer menggunakan format _snake case_ untuk nama file-nya. Contoh:

- `deploy.sh`
- `raise_brightness.sh`

**TIPS:** Command `touch` bisa digunakan untuk membuat sebuah file baru/kosongan di Unix. Command-nya adalah seperti ini:

```bash
touch belajar_shell_script.sh
# akan menghasilkan file kosong dengan nama "belajar_shell_script.sh"
```

Setelah file selesai dibuat, silahkan buka file tersebut menggunakan teks editor favorit kalian untuk mulai membuat Shell script.

Sebagai contoh, gua ingin menampilkan teks `"Hello, World!"` sebagai output setiap kali file Shell script tersebut dijalankan. Silahkan tulis line di bawah ini di dalam file Shell script yang telah dibuat.

```bash
# belajar_shell_script.sh
echo "Hello, World!"
```

**NOTE:** Setiap command yang kita bisa jalankan di terminal pada umumnya, bisa kita tuliskan di dalam Shell script.

### C. Cara menjalankan file Shell script

Untuk menjalankan file Shell script yang telah kita buat sebelumnya, kita bisa menggunakan command `bash`, diikuti dengan path/lokasi di mana file Shell script tersebut berada.

```bash
bash belajar_shell_script.sh
# silahkan sesuaikan dengan lokasi di mana file Shell script berada
```

### D. Perbedaan Shell dengan Bash

Jika kita perhatikan pada command di atas, kita menggunakan command `bash` untuk menjalankan file Shell (`.sh`). Mungkin kalian berpikir: **_"Kenapa nggak menggunakan command `sh` aja?"_**

Bash sendiri sebenarnya mirip dengan Shell. Bash adalah _superset_ dari Shell. Yang artinya Bash datang dengan fitur-fitur yang lebih banyak dibandingkan dengan Shell.

File Shell script yang telah kita buat sebenarnya bisa dijalankan dengan menggunakan command `sh`. Tapi — ini opini gua sendiri — gua lebih prefer menggunakan command `bash` untuk menjalankan file Shell script. Alasannya? Se-simple untuk menjaga _compability_ aja sih~

### E. Mengubah file Shell script menjadi _executable_

Bakal _tedious_ banget nggak sih kalo kita harus memanggil command `bash` dulu setiap kali kita mau ngejalanin file Shell script? Gimana kalo gua kasih tau ada cara untuk mempersingkat prosesnya?

Caranya adalah dengan mengubah file Shell script kita menjadi _executable_. Kita bisa menggunakan command `chmod` untuk melakukannya.

```bash
chmod +x belajar_shell_script.sh
```

Detail mengenai apa itu command `chmod`, bagaimana cara penggunaannya, dan argumen `+x`/argumen-argumen lainnya yang bisa kita gunakan mungkin akan dibahas di postingan selanjutnya, ya.

Setelah kita mengubah file Shell script tersebut menjadi _executable_, untuk menjalankannya sekarang kita hanya perlu menuliskan command di bawah:

```bash
./belajar_shell_script.sh
```

### F. Berkenalan dengan Shebang

Dengan mengubah file Shell script menjadi _executable_, sekarang kita nggak harus menuliskan command `bash` terlebih dahulu untuk menjalankannya. Kalo dipikir-pikir, kok Unix bisa tahu harus menggunakan command apa untuk menjalankan file Shell script tersebut?

Sepertinya, Unix sudah cukup "pintar" dan tahu harus menggunakan command apa untuk menjalankan file Shell script tersebut. Gimana kalo kita mau mastiin file Shell script tersebut wajib dijalankan dengan suatu command yang spesifik? Atau gimana kalo Unix belum cukup "pintar" dalam menebak harus menggunakan command apa untuk menjalankan suatu file yang _executable_ (selain file Shell script)?

Jawabannya adalah dengan menggunakan Shebang. Cara penggunaannya adalah dengan menambahkan line di bawah dan letakkan line tersebut di posisi teratas file Shell script (atau file-file _executable_ lainnya) yang kita punya.

```bash
#!/bin/sh
# NOTE: sesuaikan "/bin/sh" dengan path dari command yang ingin kita gunakan
```

Dengan cara ini, bisa dipastikan bahwa setiap kali kita menjalankan file Shell script _executable_ yang kita punya, command `sh` (yang berada di path `/bin/sh`)-lah yang akan digunakan.

### G. Menggabungkan command `alias` dengan file Shell script

Sedikit tips, kita bisa menggunakan _combo_ command `alias` dengan file Shell script yang kita punya. Cara ini efektif untuk menjalankan file Shell script dengan nama yang cukup panjang/terletak di folder yang sangat jauh. Contoh: `~/Projects/Scripts/Deployments/deploy_to_kubernetes.sh`.

Dengan menggunakan tutorial pada postingan [sebelumnya]({{< ref "/4-bermain-main-dengan-command-alias" >}}), kita bisa buatkan alias-nya misal seperti ini:

```bash
alias deploy-to-k8s="~/Projects/Scripts/Deployments/deploy_to_kubernetes.sh"
```

# 🍰 Desert

Untuk penjelasan detail mengenai syntax-syntax yang tersedia di Shell script mungkin akan gua share di postingan lainnya. Sembari menunggu, gua punya satu buah website unik untuk kalian belajar Shell script lebih lanjut, yang bisa di akses melalui halaman ini: [https://devhints.io/bash](https://devhints.io/bash).
