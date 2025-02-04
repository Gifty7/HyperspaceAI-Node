# Panduan Instalasi dan Pengaturan Node Hyperspace

Ikuti langkah-langkah berikut untuk menginstal dan menjalankan node AIOS di VPS Anda.

Sebelumnya Kunjungi https://node.hyper.space dan buat akun.
Salin private key yang diberikan dan simpan dengan aman

### Instalasi Hyperspace Node

##. **Unduh dan instal AIOS**:
   Jalankan perintah berikut untuk mengunduh dan menginstal AIOS Node:
   
   ```bash
   curl https://download.hyper.space/api/install | bash
   ```
   lanjut
   
   ```bash
   source /root/.bashrc
   ```

##. Buat file my.pem untuk menyimpan private key Anda

  ```bash
  nano my.pem
  ```
  Paste Private key dan simpan. Ctrl + X + Y
  ```bash
  chmod 600 my.pem
  ```

##. Buat sesi screen untuk menjalankan node:

   ```bash
   screen -S hyperspace
   ```
   Jalankan
   
   ```bash
   aios-cli start
   ```
CTRL + A+ D Untuk keluar Screen

##. Pilih Model dan Tier dan Cek model yang tersedia:

   ```bash
   aios-cli models available
   ```
  Pilih Model dan Tier sesuai spek vps yang anda pakai. disini saya memakai Tier 3 sebagai contoh.

  ```bash
  aios-cli hive select-tier 3
  ```

Tambahkan model, Anda bisa menambahkan model lain yang sesuai: Misalnya, untuk model contoh ini:

  ```bash
  aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
  ```


Jalankan Prompt, Bisa buat screen baru dengan nama bebas (Opsional) ubah prompt kata-kata sesuai keinginan
  
  ```bash
  aios-cli infer --model hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf --prompt "Can you explain the concept of hyperspace and its applications in science fiction?"
  ```

  ```bash
  aios-cli hive infer --model hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf --prompt "Hello, airdropnode! Can you explain hyperspace and its connection to modern science?"
  ```

##. Impor Private Key dan Login

  ```bash
  aios-cli hive import-keys ./my.pem
  ```

Login

  ```bash
  aios-cli hive login
  ```

  ```bash
  aios-cli hive connect
  ```

##. Cek Points

  ```bash
  aios-cli hive points
  ```
##. Cek Private key dan Public Key

  ```bash
  aios-cli hive whoami
  ```
## Jika Node stop, Restart

  ```bash
  aios-cli kill
  ```

Masuk Screen

  ```bash
  screen -r hyperspace
  ```

  ```bash
  aios-cli start --connect
  ```

## Untuk lebih lengkapnya anda bisa merujuk pada sumber official
https://github.com/hyperspaceai/aios-cli/tree/main

## Follow me 
https://x.com/amrit12005
