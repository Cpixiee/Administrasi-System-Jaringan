**Konfigurasi WireGuard**

yang dibutuhkan 

  1.WireGuard Server (debian)

  2.WireGuard Client (Windows)

  Download Wireguard Client : [Wireguard](https://download.wireguard.com/windows-client/wireguard-installer.exe)

Masuk Ke dalam Konfigurasi 

*1.Buatlah Virtual Machine*

*2.Setelah itu lalukan Upadate ke Mesin Kalian*

```apt Update```

Pastikan Kalian Sudah Connect Ke Bridge Dan Mendapatkan Internet

*3.Setelah Itu Kalian Install WireGuard Untuk Server*

```apt install wireguard iptables -y```

*4.MasukLah Ke Dalam Directory WireGuard*

```cd /etc/wireguard/```

*5.Buatlah PublicKey Dan Private Untuk WireGuard Server*

```wg genkey | tee privatekey | wg pubkey | tee publickey```

**NOTE**:Cara Agar Wireguard Server Dan WireGuard Client Bisa Terhubung, Kalian Harus Menukar PublicKey Server Dan PublicKey Client*

*6.Jika sudah Dibuat, Maka Akan Ada file PublicKey dan PrivateKey coba kalian ls -la*

|  |  ls -la | |
|:--------|:----------------------:|--------:|
|drwx------   |       2 root root 4096 May      |    15 08:33 |
| -rw-r--r--     |        1 root root   45 May 15 07:30     |     privatekey|
|-rw-r--r--    |        1 root root   45 May 15 07:30   |   publickey|


*7.Jika Sudah Buatlah File wg0*

```touch wg0.conf```

File wg0 adalah Konfigurasi WireGuard Untuk Wireguard Server

*8.Setelah itu edit dan Ubah, Ikuti Tempelate yang saya buat*

```nano /etc/wireguard/wg0.conf```

**Di bawah Ini Templatenya**


