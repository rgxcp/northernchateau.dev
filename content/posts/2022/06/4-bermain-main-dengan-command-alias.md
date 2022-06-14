---
title: "Bermain-main dengan Command alias"
date: 2022-06-14T18:25:50+07:00
draft: true
---

```ruby
puts "Why waste time say lot word when few word do trick?"
```

# 🥑 Appetizer

Sebagai seorang _software engineer_ yang baik, kita jangan sampai takut untuk **_"hidup"_** di terminal. Terlepas dari image **_"cool"_** yang akan kita dapatkan, dengan terbiasa hidup di terminal juga akan membuat pekerjaan kita jadi lebih cepat. Karena kita tidak bergantung lagi dengan aplikasi GUI yang _resource heavy_ hanya untuk melakukan sesuatu yang simple. Namun, ada satu _downside_ dari penggunaan terminal, yaitu saat menjalankan command dengan argumen yang panjang. Nah, command `alias` di sini bisa membantu problem kita tersebut.

# 🥩 Main Course

A. Apa itu command `alias`?

Mungkin nama command ini sudah sangat _self explanatory_. [`alias`](<https://en.wikipedia.org/wiki/Alias_(command)>) adalah sebuah command standard yang disediakan oleh sistem operasi berbasis Unix. Fungsi utamanya adalah tidak lain dan tidak bukan untuk membuat **"alias"**, duh 🙄

Untuk lebih jelasnya, dengan command `alias` ini kita bisa mengubah cara menjalankan/pemanggilan sebuah command dengan cara yang kita mau. Masih bingung? Coba langsung kita praktekin aja di bawah!

B. Cara menggunakan command `alias`

Secara sederhana, begini cara menggunakan command `alias`:

```bash
alias nama-alias="command-yang-ingin-dijalankan"
```

**NOTES:** Untuk `nama-alias` yang akan kita buat harus digabung dan tidak boleh dipisah. Bisa digabung dengan underscore (`_`), hyphen (`-`), atau karakter-karakter lainnya. Untuk `command-yang-ingin-dijalankan`, jika command-nya hanya terdiri dari satu kata, maka tidak perlu kutip, selain itu perlu. Kutip yang digunakan bisa _single_ maupun _double quote(s)_.

Sebagai contoh, gua pingin membuat alias untuk salah satu command `git` yang lumayan sering gua pakai ini: `git reset --soft HEAD~1`. Bakal cape banget kan kalo kita harus tulis manual command tersebut terus-terusan? Nah, mari kita coba buatkan aliasnya dengan nama `grsh1`. Silahkan jalankan command di bawah ini dengan terminal favorit kalian.

```bash
alias grsh1="git reset --soft HEAD~1"
```

Setelah itu, untuk memanggil alias tersebut, kita hanya perlu menuliskan `grsh1` kemudian tekan `Enter`.

```bash
grsh1
```

Alias tersebut saat dipanggil — _under the hood_ — akan menjalankan command `git reset --soft HEAD~1`.

C. Membuat `alias` _persisted_

Perlu diingat, jika kita menggunakan cara di atas, alias tersebut hanya akan valid untuk sesi terminal di mana alias tersebut dibuat. Jika kita membuka sesi terminal baru, maka alias `grsh1` tersebut akan hilang dan tidak bisa digunakan lagi.

Untuk membuatnya _persisted_ di setiap sesi terminal yang kita punya, kita bisa mendefinisikan alias yang ingin kita buat di dalam _config file-Shell_ yang kita gunakan.

1. Mengetahui Shell yang kita gunakan

Cukup _print_ value dari variable `$SHELL` yang kita punya dengan menggunakan command `echo`.

```bash
echo $SHELL
# /bin/zsh
```

Berdasarkan output dari command di atas, Shell yang gua pakai adalah `zsh`. Cukup _tricky_ (baca: gua aja yang belum tau caranya 😅) untuk mengetahui di mana letak config file-nya. Untuk `zsh` sendiri biasanya ada di `~/.zshrc`. Untuk `bash`, biasanya ada di `~/.bashrc`.

2. Membuat `alias` _persisted_ dengan cara simple

```bash
echo "grsh1='git reset --soft HEAD~1'" >> ~/.zshrc
# NOTE: ganti `~/.zshrc` sesuai dengan config file-Shell yang kalian gunakan
```

Maksud dari command di atas adalah, kita akan meng-_ouput_ teks `grsh1='git reset --soft HEAD~1'` dengan menggunakan command `echo`, kemudian menambahkan teks tersebut ke akhir file `~/.zshrc` dengan menggunakan command `>>`.

3. Membuat `alias` _persisted_ dengan cara ribet

Seperti kata orang kebanyakan, ngapain pakai cara yang simple kalo ada cara yang ribet, kan?

Untuk cara "ribet" ini, caranya cukup buka _config file-Shell_ yang kalian gunakan dengan teks editor favorit kalian. Kemudian tuliskan line ini di posisi paling bawah file tersebut (posisinya bebas sih sebenernya~).

```bash
# config file-Shell (contoh: ~/.zshrc)
alias grsh1="git reset --soft HEAD~1"
```

D. Trivia

Setiap kali kita merubah _config file-Shell_ yang kita gunakan, kita bisa meload perubahan yang sudah kita buat tanpa harus menutup-membuka kembali terminal. Caranya adalah dengan menggunakan command `source` dengan cara seperti ini:

```bash
source /path/to/config-file
# contoh: source ~/.zshrc
```

# 🍰 Desert

Terus gimana kalo alias yang mau kita buat panjang, terdiri dari beberapa baris, dan mungkin harus ada conditional statement-nya? Cara di atas sebenernya masih valid untuk digunakan. Tapi, kalo gua sendiri sih lebih prefer untuk pakai cara yang kedua. Apa itu? Tunggu post selanjutnya, ya!
