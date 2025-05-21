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
Kamu menjalankan Node Penambang berbasis CPU secara lokal. Ini memerlukan perangkat keras yang cukup kuat

Ikuti panduan [CLI Setup](

### Method 1: Solo (CLI):
* You run a solo CPU-based Miner Node on your system which will certainly need a powerful hardware.
* You can follow [CLI Setup](https://github.com/0xmoei/nockchain/blob/main/README.md#cli-miner-setup) steps.

### Method 2: Pool & Method 3: GUI
* You join a pool (same as bitcoin mining), share your computational power and earn rewards in a shared pool of rewards.
* Official mining method is CLI introduced by the team, and no official Pool or GUI mining programs introduced.
* But new community-driven *Projects* and *Pools* are poping up.
* **GUI Setup (App)**: There's a new project called [**Nockpool**](https://swps.io/nockpool), I think they are building a GUI-based Node so you can easily open a wallet on Windows, join a pool, and Mine $NOCK.

![image](https://github.com/user-attachments/assets/6f58647d-2255-4ebb-839c-eeb539cac258)

---

# CLI Miner Setup
## Hardware Requirements
Hardware requirement is highly speculative since no one knows how Mainnet-launch goes.

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

* more CPU = more hashrate = more chances
* We still can't say that's enough, because it's just a testnet environment and we need to wait until mainnet.

---

## OS Requirements

* **Windows Users:** Install Linux Ubuntu on your Windows using this [Guide](https://github.com/0xmoei/Install-Linux-on-Windows)
* **VPS:** Recommended crypto-payment VPS provider to [Purchase](https://my.hostbrr.com/order/forms/a/NTMxNw==) or Visit [VPS Beginner Guide](https://github.com/0xmoei/Linux_Node_Guide/)

> Note: Miners are initially CPU-based for users and will eventually move to GPU and ASIC.
>
> Zorp as a for-profit labs company behind Nockchain will be selling private, closed-source software to mining partners, possibly even GPU-based to help bootstrap the initial security and proofrate of the network.
>
> Meaning they will likely dominate block rewards over the vast majority of people, but yet the protocol might potentially be rewarding for early users.

---

## CLI Installation Steps
### Step 1: Install Dependecies
* Update Packages
```bash
sudo apt-get update && sudo apt-get upgrade -y
```
* Install Packages:
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

* Docker (For Mainnet, we might choose Docker setup)
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

### Step 2: Clone NockChain Repo
```bash
git clone https://github.com/zorp-corp/nockchain

cd nockchain
```

### Step 3: Install Choo (Jock/Hoon Compiler)
```bash
make install-hoonc
```
* This compiles `hoonc`, the Nock-based compiler used for running Jock programs and ZKVM applications.
  
### Step 4: Build
Building may take more than 15 minutes.
```bash
# Install node binaries
make build

# Install wallet binaries
make install-nockchain-wallet

# Install Nockchain
make install-nockchain
````

## Step 5: Setup Wallet
Make sure you are in `nockchain` directory.
* Set PATH:
```bash
export PATH="$PATH:$(pwd)/target/release"
```
* Create wallet:
```bash
nockchain-wallet keygen
```
* Save `memo`, `private key` & `public key` of your wallet.
> Note: After every terminal restart, Ensure you execute these two commands before executing wallet commands again: `cd nockchain` & `export PATH="$PATH:$(pwd)/target/release"`.  By doing this, you won't get Error: `wallet: command not found`.

## Step 6: Configure Nodes
Your Node's configuration is in `Makefile`
Open `Makefile`:
```bash
nano Makefile
```
* `MINING_PUBKEY`: Replace your wallet `public key` with its value.
* `Ports`: By default, Nodes use ports `3005` and `3006`. If these ports are occupied on your system, modify them in the node configuration.
* To save: `Ctrl+X` + `Y` + `Enter`

### Step 7: Open ports
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

### Step 8: Run Leader Node
Leader Node is a fake testnet node. On mainnet Peer IDs will be replaced with Leader node, we only need to run Follower Node in the next step.
* Open a screen:
```bash
screen -S leader
```
* Start a **Leader Node** (Testnet Node for fake genesis block):
```bash
make run-nockchain-leader
```
* Wait for it to install.
* To minimize:  `Ctrl` + `A` + `D`

### Step 9: Run Follower Node:
* Open a screen
```bash
screen -S follower
```

* Start a **Follower Node** (Miner Node for connecting to other peers):
```bash
make run-nockchain-follower
```
```console
# OK Response:
I (12:18:31) "inner dumbnet cause: [%command %timer]"
I (12:18:32) nc: block by-height: [Ok(%heavy-n) Ok(1) 0]
```
* To minimize:  `Ctrl` + `A` + `D`

## Usefull commands
### Wallet commands:
> Note: After every terminal restart, Ensure you execute these two commands before executing wallet commands again: `cd nockchain` & `export PATH="$PATH:$(pwd)/target/release"`.  By doing this, you won't get Error: `wallet: command not found`.

General Wallet Command:
```bash
nockchain-wallet --nockchain-socket ./test-leader/nockchain.sock
```
Wallet Balance:
```bash
nockchain-wallet --nockchain-socket ./test-leader/nockchain.sock balance
```
* It looks good. `~` is like a 0 and balance will be 0 until you mine a block.

![image](https://github.com/user-attachments/assets/52550e55-21b2-4625-84f9-3250eca367f5)

* [Official repo](https://github.com/zorp-corp/nockchain/blob/master/crates/wallet/README.md) for more Wallet commands.

### Screen commands:
Ensure screens do not overlap. Before opening or switching to another screen, minimize or close the current screen.
```console
# Return leader screen (leader logs)
screen -r leader

# Return leader screen (follower logs)
screen -r follower

# Minimize screen
Press: CTRL + A + D

# Screens list
screen -ls

# Stop Node when inside a screen
Press: Ctrl + C

# Kill and Remove screen when outside a screen (replace NAME)
screen -XS NAME quit
```

---

Well, We just tested a Nockchain Miner node on the testnet, which is *NOT incentivized*. This was an experiment to prepare for the Mainnet launch on **May 19**. The team might update the docs with new features, and the Mainnet setup may ir may not differ.

---


# Nockchain

**Nockchain adalah blockchain ringan yang dirancang untuk aplikasi berat yang membutuhkan verifikasi tinggi.**

Kami percaya bahwa masa depan blockchain ada di sistem yang ringan namun dapat menyelesaikan komputasi kompleks secara terverifikasi. Cara mencapainya bukan dengan menyalin data ke semua node publik, tapi dengan pembuktian privat off-chain yang kemudian diverifikasi secara on-chain.

*⚠️ Catatan: Nockchain masih bersifat eksperimental dan belum diaudit sepenuhnya. Gunakan dengan risiko Anda sendiri.*


## 🔧 Persiapan Awal (Install Paket)
```
sudo apt update && sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```

## Install RUST
Nockchain dibangun dengan Rust. Kamu perlu menginstal rustup terlebih dahulu: [Tutorial install Rust di Linux & WSL](https://github.com/kajijp/Install-RUST-di-WSL-dan-Linux)
<br>Ikuti petunjuk di halaman tersebut sesuai sistem operasi kamu (Windows, macOS, Linux).
```
curl https://sh.rustup.rs -sSf | sh
```
```
source $HOME/.cargo/env
```
## Salin Repositori zorp-corp
```
git clone https://github.com/zorp-corp/nockchain && cd nockchain
```
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
