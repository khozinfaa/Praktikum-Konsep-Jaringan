NAMA : Muh Khozinatul Asror
NRP : 3121600026
KELAS : 2 D4-IT-A

## Tugas minggu ke 4
## Cisco analisis Tracer

[![image.png](https://i.postimg.cc/MHh8r3cY/image.png)](https://postimg.cc/zHSMyjFL)

    Topologi di atas terdiri dari 2 pc client dan 2 router dengan subneting.

### Configuration IP (PC)
[![image.png](https://i.postimg.cc/Nj3CPN6d/image.png)](https://postimg.cc/ZWLLWxDN)

    PC 0 :
    IP Address -> 192.168.1.2
    Subnet Mask -> 255.255.255.0
    Gateway -> 192.168.1.1 (IP Router)
    PC1 :
    IP Address -> 192.168.3.2
    Subnet Mask -> 255.255.255.0
    Gateway -> 192.168.3.1 (IP Router)

### Configuration IP (Router) 
[![IPConfig-Router.png](https://i.postimg.cc/j5wkCGQB/IPConfig-Router.png)](https://postimg.cc/PpHMRV7M)
  
    Router 0 :
    Interface Gig0/0/0 -> 192.168.1.1/24 (Configuration for pc client)
    Interface Gig0/0/1 -> 192.168.2.1/24 (Configuration for routing)
    Router 1 :
    Interface Gig0/0/0 -> 192.168.3.1/24 (Configuration for pc client)
    Interface Gig0/0/1 -> 192.168.2.2/24 (Configuration for routing)

### Configuration Static Route (Router)
[![image.png](https://i.postimg.cc/9Qf3VqT9/image.png)](https://postimg.cc/fJ1qfy8W)
   
    Untuk setting static routing di cisco packet tracer menggunakan perintah :
    #ip route [destination] [subnet] [next hop address]
    Keterangan :
    - ip route : perintah membuat tabel routing static
    - destination : network jaringan yang dituju
    - subnet : subnet mask jaringan yang dituju
    - next hop address : ip dari router yang akan dilewati
    
    IP Route (Router 0) :
    192.168.3.0/24 via 192.168.2.2
    [for sending packages or ping from PC0-192.168.1.2/24 to PC1-192.168.3.2/24]
    IP Route (Router 1) :
    192.168.1.0/24 via 192.168.2.1
    [for sending packages or ping from PC1-192.168.3.2/24 to PC0-192.168.1.2/24]

### Test Ping From Network 192.168.1.0/24 To 192.168.3.0/24 Or Reverse
[![image.png](https://i.postimg.cc/m2xsGD2Z/image.png)](https://postimg.cc/bdRMxqt4)
  
    Terlihat gambar di atas PC1-192.168.3.2/24 tidak memalukan request ping dan hanya replay ping sebelumnya dari PC0-192.168.1.2/24 dan sudah memiliki daftar arpa cache yaitu IP 192.168.3.1 (Router 1) dengan Physical / MAC Address 0001.9724.4801 sehingga untuk memalukan ping pada PC1-192.168.3.2/24 ke PC1-192.168.1.2/24 tidak terjadi RTO lagi.
[![image.png](https://i.postimg.cc/FsmhLztW/image.png)](https://postimg.cc/mhXxxbgC)

    RTO kedua digantikan dengan packgage broadcast dari Router 0 (192.168.2.1/24) ke Router 1 (192.168.2.2/24) untuk mendapatkan MAC / Phsyical Address. Terlihat pada arp -a (arpa cache) pada PC0 (192.168.1.2/24) memiliki daftar arp yaitu 192.168.1.1 (IP Router 0) dengan Physical / MAC Address 0090.2148.aa01.