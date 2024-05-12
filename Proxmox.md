# Materi Proxmox

*Cara uploud Iso Di Proxmox Dan intslasi IPcop*

 #*Memberikan Tutor Sekaligus Praktek*#

 **Tugas:** 
       
       ``` MainOS ip = 192.168.?.?/24
        
        Proxmox Server = 192.168.?.?+10
        
        ipcop/guest = 192.168.?.?+20```

   Standar keberhasilan atau penilaian: 

   1.SSH

   2.Ping Dari IPCOP ke MainOS dan Proxmox Serta Sebaliknya

**Setelah Install Proxmox Kalian Perlu MengRouting Agar MainOS dan Guest Bisa saling terhubung**

*caranya*

``` echo 1 > /proc/sys/net/ipv4/ip_forward ```

``` iptables -t nat -A POSTROUTING -j MASQUERADE ```

   
   * Jika Sudah Kita Tinggal Install IPCOPnya*

![](https://github.com/Cpixiee/Upload/blob/main/ss1.png)

Kalian Pilih OS yang telah Kalian Upload Seperti Gambar Di Atas Dan Juga Kernel Digant Ke 2.4 

![](https://github.com/Cpixiee/Upload/blob/main/ss2.png)

setelah itu SCCI Contorllernya di ganti ke Default

![](https://github.com/Cpixiee/Upload/blob/main/ss3.png)

Network Nya ikuti Saja Sesuai Gambar

**jika sudah Di upload kalian start consolenya disini saya akan mengberitahu step yang penting saja**

![](https://github.com/Cpixiee/Upload/blob/main/ipcop1.png)

Pilih Hardisk

![](https://github.com/Cpixiee/Upload/blob/main/ipcop2.png)

Disini Kalian Skip Saja 

![](https://github.com/Cpixiee/Upload/blob/main/ipcop3.png)

Disini Kalian Tidak Perlu Mengceklis atau Memberi Tanda * Cukup Kita **ok** Saja

![](https://github.com/Cpixiee/Upload/blob/main/ipcop4.png)

Pilih *Select**

![](https://github.com/Cpixiee/Upload/blob/main/ipcop5.png)

Pilih "GREEN" dan Lalu assign

![](https://github.com/Cpixiee/Upload/blob/main/ipcop6.png)

Jika Di Table Sudah Muncul **GREEN** Setelah itu Pencet **DONE**

![](https://github.com/Cpixiee/Upload/blob/main/ipcop6.png)

 Arahkan ke "Ok" enter

![](https://github.com/Cpixiee/Upload/blob/main/ipcop7.png)

Masukan Ip Kalian Sesuaikan Netwok Id IP kalian dengan AP Yang kalian Pakai

![](https://github.com/Cpixiee/Upload/blob/main/ipcop8.png)

Disini Kalian Tidak Perlu Mengatur DHCPnya Kalian Biarkan Saja Lalu Tekan **SKIP**


![](https://github.com/Cpixiee/Upload/blob/main/ipcop9.png)

*Disini Instalasi Sudah Selesai Sekarang Kita Tinggal Mengatur SSH Di IPCOPnya, Sebelum itu Kalian login terlebih Dahulu Jika Sudah 
kalian Kedalam Tampilan GUI IPCOP dengan cara: https://(ipkalian):8443 setelah itu kalian masukan dengan* 

Login: **Admin**

password: **yang kalian buat**

Contohnya Seperti Di gambar Di bawah ini 

![](https://github.com/Cpixiee/Upload/blob/main/ipcop10.png)

Kalian Pilih System Lalu Cari Bagian SSH Server Kalian Allow Semua / Kalian Ceklis Seperti Gambar Di Bawah ini

![](https://github.com/Cpixiee/Upload/blob/main/ipcop11.png)

Setelah Itu Kalian Login SSH dengan menggunakan Termial Windows/MX linux/Ubuntu dll.

![](https://github.com/Cpixiee/Upload/blob/main/ipcop12.png)

Jika Sudah Login Coba Kalian Ping Ke MainOS dan Ke Proxmox Sever Apakah Bisa 

**TroubleShoot**

Disini Saya akan memberikan Sedikit Cara mengatasi TroubleShoot Di Server Proxmox

**1.kenapa Dari IPCOP ping / Paket Yang Kita Kirim Tidak Masuk**

2.Kenapa Saat SSH ada tulisan *WARNING* 

Oke Kita Bahas Yang Pertama DuluKemungkinan kenpa Kalian Tidak Bisa mengping ke MainOS dari IPCOP itu karna ROUTING Kalian Belum 
berhasil kalian dapat mengeceknya dengan menggunakan comment

``` iptables -t nat -nvL```

contoh nya seperti ini

![](https://github.com/Cpixiee/Upload/blob/main/ss%20ssh%20nvl.png)

jika kalian lihat disitu tidak ada sama sekali ROUTING, Jadi kalian Perlu Meng ROUTING ulang 

jika ada maka tampilannya seperti ini

![](https://github.com/Cpixiee/Upload/blob/main/ada.png)

Jika Belum bisa Juga Berati Kalian perlu mematikan **FIREWALLnya**, Kenapa Firewall?? 

Disini Saya akan memberikan Penjelasan Terhadap defense yang dilakukan oleh firewall 

**disini Jika firewall kalian aktif maka dia akan mengira ping/paket yang kalian kirim adalah paket yang berbahaya jadi otomatis paket 
yang kalian kirim akan di tahan dan di hapus oleh firewall**

cara mengatasi cukup mudah kalian hanya perlu ke pengaturan windows lalu cari firewall network Protections lalu matikan semuanya
Matikan Seperi gambar Di bawah ini

![](https://github.com/Cpixiee/Upload/blob/main/firewall.png)

jika kalian ping maka paket yang kalian kirim akan masuk, contohnya seperti gambar di bawah ini

![](https://github.com/Cpixiee/Upload/blob/main/firewall%20not%20active.png)

jika firewall di aktifkan maka akan terjadi seperti ini, jadian gambar di bawah ini dan di atas sebagai perbandingan 

![](https://github.com/Cpixiee/Upload/blob/main/firewall%20aktive.png)

*Selanjutnya kita masuk ke trouble shooting yang kedua ini terjadi tidak hanya di proxmox saja*

pertama kalian pergi ke file exploler kalian, ikuti saja langkah - langkah di bawah ini

buka tampilan this pc dan pilih disk kalian

![](https://github.com/Cpixiee/Upload/blob/main/thispc1.png)

jika sudah pilih user 

![](https://github.com/Cpixiee/Upload/blob/main/thispc2.png)

pilih user yang kalian punya disini user saya salwi

![](https://github.com/Cpixiee/Upload/blob/main/thispc3.png)

jika sudah pilih .ssh dan masuk ke dalam foldernya

![](https://github.com/Cpixiee/Upload/blob/main/thispc4.png)

jika sudah hapus file yang unknown host

![](https://github.com/Cpixiee/Upload/blob/main/thispc5.png)

jika sudah kalian coba login lagi menggunakan ssh 

*SEKIAN TERIMAKASIH

