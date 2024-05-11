# Materi Proxmox

*Cara uploud Iso Di Proxmox Dan intslasi IPcop*

 #*Memberikan Tutor Sekaligus Praktek*#

 **Tugas:** 
       
        MainOS ip = 192.168.?.?/24
        
        Proxmox Server = 192.168.?.?+10
        
        ipcop/guest = 192.168.?.?+20

   Standar keberhasilan atau penilaian: 

   1.SSH

   2.Ping Dari IPCOP ke MainOS dan Proxmox Serta Sebaliknya

**Setelah Install Proxmox Kalian Perlu MengRouting Agar MainOS dan Guest Bisa saling terhubung**

*caranya*

```echo 1 > /proc/sys/net/ipv4/ip_forward```

```iptables -t nat -A POSTROUTING -j MASQUERADE```


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
      
