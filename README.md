## Nockchain
Nockchain adalah blockchain ringan untuk komputasi berat. Ia menggunakan Zero-Knowledge Proof of Work (zkPoW). Penambang membuat Zero-Knowledge Proof (ZKP) dari perhitungan teka-teki tetap, kemudian melakukan hash terhadap ZKP tersebut, dan mendapatkan $NOCK berdasarkan kekuatan komputasi mereka.

Tim telah merilis Public Testnet untuk menjalankan ***node testnet lokal*** dan ***penambang testnet***, agar pengguna bisa menjelajahi cara kerja Nockchain sebelum peluncuran Mainnet.
---

## Tentang $NOCK
- Penambangan dimulai tanggal 21 Mei. [Countdown Peluncuran](https://nockstats.com/)
- Total Supply: 2^32 nocks (Sekitar 4.29 B).
- Fair launch: 100% $NOCK akan didistribusikan ke Penambang.
- $NOCK digunakan untuk membayar ruang blok (blockspace) di Nockchain.

---

## Detail Jaringan Mainnet
- Mainnet akan diluncurkan pada 21 Mei
- Waktu blok 10 menit (seperti Bitcoin)
- Di Testnet, kita menjalankan *"Miner"* dan *"node testnet lokal simulasi"* dengan **blok genesis palsu**, agar Miner bisa terhubung
- Setelah Mainnet aktif, **peer publik** akan diumumkan, jadi kita hanya perlu menjalankan Miner
- Sebelum peluncuran Mainnet, tim akan memperbarui [Repositori Resmi](https://github.com/zorp-corp/nockchain) dengan informasi seperti URL peer publik untuk menghubungkan miner

---

## Detail Distribusi $NOCK
- **Semakin awal** kamu mulai menambang, semakin **BESAR** reward yang akan kamu dapatkan.

![image](https://github.com/user-attachments/assets/88a088b9-f082-45ae-9ffe-90009a713bfb)

---

## Dashboard Penambangan Nock
Dashboard komunitas ini, [**NockStats**](https://nockstats.com/), memiliki fitur seperti: Saldo Wallet, Perdagangan, Tokenomik, Kalkulator, dll.

---

## Cara Menambang
* Mekanisme penambangan sama persis dengan Bitcoin (Proof of Work)
* Semakin besar kekuatan komputasi = Semakin besar reward
* Semakin banyak penambang = Hashrate meningkat = Tingkat kesulitan bertambah

### Metode 1: Solo (CLI):
* Kamu menjalankan Node Penambang berbasis CPU secara lokal. Ini memerlukan perangkat keras yang cukup kuat
* Ikuti panduan [CLI Setup](https://github.com/kajijp/nockchain/blob/master/README.md#cli-miner-setup)

### Metode 2: Pool & Metode 3: GUI
* Kamu bisa bergabung dengan mining pool, berbagi kekuatan komputasi dan mendapatkan reward bersama
* Metode resmi yang dirilis tim hanya versi CLI, belum ada GUI atau Pool resmi
* Namun, proyek dan pool berbasis komunitas mulai bermunculan
* **GUI Setup (Aplikasi)**: Ada proyek baru bernama [**Nockpool**](https://swps.io/nockpool) yang sedang mengembangkan GUI berbasis Windows agar mudah menambang $NOCK


![image](https://github.com/user-attachments/assets/6f58647d-2255-4ebb-839c-eeb539cac258)

---

# CLI Miner Setup
## Spesifikasi Hardware
Spesifikasi perangkat keras masih bersifat spekulatif karena belum ada acuan pasti hingga Mainnet aktif.

<table>
  <tr>
    <th colspan="3">Miner is CPU-based initially</th>
  </tr>
  <tr>
    <td>RAM</td>
    <td>CPU</td>
    <td>Disk</td>
  </tr>
  <tr>
    <td><code>64 GB</code></td>
    <td><code>6 cores or higher</code></td>
    <td><code>100-200 GB SSD</code></td>
  </tr>
</table>

* Semakin besar CPU = Semakin tinggi hashrate = Semakin besar peluang
* Masih belum bisa dipastikan apakah ini cukup, karena ini masih testnet.
---

## Persyaratan OS

* **Pengguna Windows:** Instal Ubuntu di Windows menggunakan panduan ini: [Install Linux on Windows](https://github.com/0xmoei/Install-Linux-on-Windows)
* **VPS:** Gunakan penyedia VPS andalan kalian

> Catatan: Awalnya penambangan dilakukan menggunakan CPU, tetapi nanti akan beralih ke GPU dan ASIC
Zorp (perusahaan di balik Nockchain) akan menjual perangkat lunak penambangan tertutup ke mitra GPU, sehingga mereka kemungkinan mendominasi reward.
> 
---

## CLI Installation Steps
### Langkah 1: Install Dependecies
* Perbarui Paket
```bash
sudo apt-get update && sudo apt-get upgrade -y
```
* Install Paket:
```bash
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```
* Rust:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
```bash
source $HOME/.cargo/env
```

* Docker (Untuk Mainnet, Instal Docker (untuk Mainnet nanti))
```bash
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker
sudo docker run hello-world

sudo systemctl enable docker
sudo systemctl restart docker
```

### Langkah 2: Salin NockChain Repositori
```bash
git clone https://github.com/zorp-corp/nockchain

cd nockchain
```

### Langkah 3: Install Choo (Jock/Hoon Compiler)
```bash
make install-hoonc
```

### Langkah 4: Build
Build biasanya memakan waktu sekitar 15 menit.
```bash
# Install binary node
make build

# Install binary wallet
make install-nockchain-wallet

# Install Nockchain
make install-nockchain
````

## Langkah 5: Setting Wallet
Make sure you are in `nockchain` directory.
* Set PATH:
```bash
export PATH="$PATH:$(pwd)/target/release"
```
* Create wallet:
```bash
nockchain-wallet keygen
```

* Simpan memo, private key, dan public key.
> Setelah restart terminal: jalankan kembali cd nockchain dan export PATH=... agar perintah wallet bisa dijalankan..

## Langkah 6: Konfigurasi Node
Konfigurasi node kalian berada di `Makefile`
Buka `Makefile`:
```bash
nano Makefile
```
* `MINING_PUBKEY` : Ganti `MINING_PUBKEY` dengan `public key` dari wallet kamu.
* `Ports`: Jika port 3005 & 3006 sudah digunakan, ubah ke port lain
* Tekan `Ctrl+X` + `Y` + `Enter` untuk menyimpan

### Langkah 7: Membuka ports
```console
# Allow ssh port
sudo ufw allow ssh
sudo ufw allow 22

# Enable firewall
sudoufw enable

# Open ports
sudo ufw allow 3005/tcp
sudo ufw allow 3006/tcp
```

### Langkah 8: Menjalan Leader Node
Leader Node adalah node testnet palsu. Pada mainnet nanti, Peer ID akan digantikan dengan Leader node, sehingga kita hanya perlu menjalankan Follower Node di langkah selanjutnya.
* Membuka screen:
```bash
screen -S leader
```
* Memulai **Leader Node** (Testnet Node untuk genesis block palsu):
```bash
make run-nockchain-leader
```
* Tunggu proses instalasinya.
* Untuk mengecilkan screen(keluar tanpa stop):  `Ctrl` + `A` + `D`

### Langkah 9: Menjalankan Follower Node:
* Membuka screen:
```bash
screen -S follower
```

* Memulai **Follower Node** (Miner Node untuk menghubungkan dengan peer lain):
```bash
make run-nockchain-follower
```
```console
# OK Response:
I (12:18:31) "inner dumbnet cause: [%command %timer]"
I (12:18:32) nc: block by-height: [Ok(%heavy-n) Ok(1) 0]
```
* To minimize:  `Ctrl` + `A` + `D`

## Commands Berguna
### Wallet commands:

> Catatan: Setelah setiap kali terminal direstart, pastikan untuk menjalankan dua perintah ini sebelum menjalankan perintah wallet kembali: `cd nockchain` & `export PATH="$PATH:$(pwd)/target/release"`. Dengan melakukan ini, kamu tidak akan mendapatkan error: `wallet: command not found`.

Perintah Wallet Umum:
```bash
nockchain-wallet --nockchain-socket ./test-leader/nockchain.sock
```
Cek Saldo Wallet:
```bash
nockchain-wallet --nockchain-socket ./test-leader/nockchain.sock balance
```
* Tampilan saldo akan terlihat seperti ~ yang artinya 0. Saldo akan tetap 0 sampai kamu berhasil menambang satu blok.

![image](https://github.com/user-attachments/assets/52550e55-21b2-4625-84f9-3250eca367f5)

* [Repositori Resmi](https://github.com/zorp-corp/nockchain/blob/master/crates/wallet/README.md) untuk lebih banyak perintah Wallet.

### Perintah Screen:
Pastikan tidak ada screen yang tumpang tindih. Sebelum membuka atau berpindah ke screen lain, minimalkan atau tutup screen yang sedang aktif terlebih dahulu.
```console
# Kembali ke leader screen (leader logs)
screen -r leader

# Kembali ke leader screen (follower logs)
screen -r follower

# Mengecilkan screen
Press: CTRL + A + D

# Daftar Screens
screen -ls

# Menghentikan node didalam screen
Tekan: Ctrl + C

# Hapus dan tutup screen saat berada di luar screen (ganti NAME dengan nama screen)
screen -XS NAMA quit
```

---

Kita baru saja menguji node Miner Nockchain pada testnet, yang *TIDAK memberikan insentif*. Ini adalah percobaan untuk persiapan peluncuran Mainnet pada **19 Mei**. Tim pengembang kemungkinan akan memperbarui dokumentasi dengan fitur-fitur baru, dan setup pada Mainnet bisa saja berbeda atau sama dengan testnet.

---



<br><br><br>
🔥 Mohon dukungan agar KajiJP semakin berkembang, like dan gabung ke channel kami, sebarkan dan undang teman anda, terima kasih, Insyaallah JP!
## 🌐 Komunitas KajiJP
Gabung dan ikuti info terbaru:
- 💬 [Telegram](https://t.me/kajijp)
- 🎮 [Facebook](https://facebook.com/kajijp)
- 🐦 [X / Twitter](https://x.com/wakkajijp)
- ▶️ [Yourube](https://www.youtube.com/@KajiJP)
