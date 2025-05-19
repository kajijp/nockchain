# Nockchain

**Nockchain adalah blockchain ringan yang dirancang untuk aplikasi berat yang membutuhkan verifikasi tinggi.**

Kami percaya bahwa masa depan blockchain ada di sistem yang ringan namun dapat menyelesaikan komputasi kompleks secara terverifikasi. Cara mencapainya bukan dengan menyalin data ke semua node publik, tapi dengan pembuktian privat off-chain yang kemudian diverifikasi secara on-chain.

*⚠️ Catatan: Nockchain masih bersifat eksperimental dan belum diaudit sepenuhnya. Gunakan dengan risiko Anda sendiri.*


## 🔧 Persiapan Awal (Setup)

Nockchain dibangun dengan Rust. Kamu perlu menginstal rustup terlebih dahulu: [https://rustup.rs/](https://rustup.rs/)
<br>Ikuti petunjuk di halaman tersebut sesuai sistem operasi kamu (Windows, macOS, Linux).

## Instal Kompiler Hoon (hoonc)
Setelah Rust terinstal, jalankan perintah berikut untuk menginstal hoonc:

```
make install-hoonc
```

## Bangun Proyek Nockchain dan Wallet
Setelah hoonc terinstal, bangun semua file biner (termasuk dompet/wallet dan aset-aset yang dibutuhkan):
```
make build
```

## 💰 Instalasi Dompet (Wallet)

Setelah kamu menyelesaikan langkah build di atas, jalankan perintah berikut untuk menginstal dompet Nockchain:

```
make install-nockchain-wallet
```
Untuk menjalankan dompet, buka file README yang ada di direktori wallet:
```
nano ./crates/nockchain-wallet/README.md
```

## ⛓ Instalasi Nockchain (Node Blockchain)

Setelah proses build, kamu juga bisa menginstal node Nockchain dengan perintah berikut:

```
make install-nockchain
```


## 🧪 Menjalankan Node Uji Coba

Kamu bisa menjalankan dua jenis node uji coba untuk melihat bagaimana Nockchain bekerja.<br>

### 🔹 Node Leader (Pemimpin)<br>
Node ini akan membuat genesis block (blok pertama dalam blockchain):<br>

```
make run-nockchain-leader
```

### 🔸 Node Follower (Pengikut)
Node ini akan menunggu sampai genesis block diterbitkan oleh leader:

```
make run-nockchain-follower
```

<br><br><br>
🔥 Mohon dukungan agar KajiJP semakin berkembang, like dan gabung ke channel kami, sebarkan dan undang teman anda, terima kasih, Insyaallah JP!
## 🌐 Komunitas KajiJP
Gabung dan ikuti info terbaru:
- 💬 [Telegram](https://t.me/kajijp)
- 🎮 [Facebook](https://facebook.com/kajijp)
- 🐦 [X / Twitter](https://x.com/wakkajijp)
- ▶️ [Yourube](https://www.youtube.com/@KajiJP)
