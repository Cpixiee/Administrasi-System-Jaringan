**Konfigurasi WireGuard**

yang dibutuhkan 

  1.WireGuard Server (debian)

  2.WireGuard Client (Windows)

  Download Wireguard Client : [Wireguard](https://download.wireguard.com/windows-client/wireguard-installer.exe)

**#####Konfigurasi WireGuard Server#####**

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

Publickey di Client

![](https://github.com/Cpixiee/Upload/blob/main/Publickey.png)

*Ini Templatenya :*[Templatenya](https://github.com/Cpixiee/Administrasi-System-Jaringan/blob/main/code%20github1.1txt.txt)

Ubah Seperti Di bawah ini Address Menyesuaikan Soal 

Port Juga Bisa di ganti lalu add dengan menggunakan UFW (optional)

![](https://github.com/Cpixiee/Upload/blob/main/wgo.png)

*9.Jika sudah kalian edit sysctl.conf bisa juga manual*

```nano /etc/sysctl.conf```

Ganti Seperti Di Gambar di Bawah ini

![](https://github.com/Cpixiee/Upload/blob/main/systcl.png)

jika sudah jalankan comment ini

```sysctl -p```

*10.jika sudah kita start dan aktifkan wireguardnya, jalankan comment di bawah ini*

```systemctl start wg-quick@wg0.conf.service```

```systemctl enable wg-quick@wg0.conf.service```

*11.lalu kita set peer untuk clientnya*

 wg set wg0 peer (PublicKey client windows) allowed-ips (ip yang akan diberikan ke windows)

contoh
```wg set wg0 peer jskjksdjkajjjsasadaderer== allowed-ips 10.10.10.2```

*12.jika sudah kita atur ROUTING nya, Salin template yang ada di bawah ini*

**Template :** [Iptables Template](https://github.com/Cpixiee/Upload/blob/main/code%20iptables.txt)

Atur Network VPN (sesuai IP yang kalian inginkan)

Jika sudah jalankan comment di bawah ini

```systemctl restart wg-quick@wg0.service```

Jika sudah urusan di Server Sudah Kelar, Tinggal kita Atur saja Clientnya

**#####Konfigurasi WireGuard Client#####**

*1.Kalian Masuk Ke Aplikasi WireGuardnya*

*2.jika sudah tambahkan tunnel, caranya seperti di gambar di bawah ini*

![](https://github.com/Cpixiee/Upload/blob/main/Wireguard%20Client.png)

Bisa juga Menggunakan : <kbd>Ctrl</kbd> + <kbd>N</kbd>

*3.Jika Sudah Tambkan Seperti Gambar Di bawah ini*, [Pakai Template ](https://github.com/Cpixiee/Upload/blob/main/codeclient.txt)

**Name untuk VPN nya bebas**

![](https://github.com/Cpixiee/Upload/blob/main/code%20.png)

Jika Sudah **SAVE**

*4.jika sudah Active kan VPN nya Seperti gambar di bawah*

![](https://github.com/Cpixiee/Upload/blob/main/active.png)

**Jika Sudah Maka Akan Berwarna Hijau Dan ada Perisainya**

**######OKEY SUDAH SELESAI KONFIGURASINYA WAKTUNYA MELAKUKAN PENGETESAN DAN PENGECEKAN***######


