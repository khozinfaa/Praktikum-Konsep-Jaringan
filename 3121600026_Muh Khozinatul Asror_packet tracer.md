NAMA : Muh Khozinatul Asror
NRP : 3121600026
KELAS : 2 D4-IT-A

## Tugas minggu ke 3
## Documentation cisco packet tracer analisis

[![image.png](https://i.postimg.cc/Znbb5qcC/image.png)](https://postimg.cc/62PJHtFX)

    gambar diatas merupakan suatu Topologi yang terdiri dari 3 pc client dan 1 hub dengan subneting yaitu 192.168.1.1 / 192.168.1.2 / 192.168.1.3 dengan icdr 24 tanpa default gateway dan dns karena tanpa router serta tidak dihubungkan ke jaringan internet.

### PC0 ke PC1 ? 
### JAWAB ->"Terjadi/perlu menggunkan broadcast"
[![image.png](https://i.postimg.cc/BQvHnTMc/image.png)](https://postimg.cc/Dmt8CXV8)

    Terlihat sebelum melakukan ping tidak ada ARP cache yang terdaftar dan setelah melakukan ping pada PC0 (192.168.1.1) ke PC1 (192.168.1.2) terlihat Arp cache pada PC0 memiliki informasi IP / Logikal Address PC1 (192.168.1.2) dengan Physical Address / MAC Address yaitu 00e0.f9d9.2340

    Sebenarnya ketika proses ping dari PC0 (192.168.1.1) ke PC1 (192.168.1.2), proses terssebut ditahan atau ditunda terlebih dahulu karena pada layer Data Link (OSI Layer - 2) belum ditemukannya MAC Address sebelum packet request (ping) dikirimkan dan untuk mencari MAC Address tersebut diperlukan Paket Broadcast dengan Broadcast Address yaitu FFFF.FFFF.FFFF.
    
[![image.png](https://i.postimg.cc/sxnMFLWQ/image.png)](https://postimg.cc/gLZz8NNm)

     Broadcast itu sendiri adalah proses mengirimkan sebuah paket kepada semua device yang terhubung dalam satu area jaringan subneting dari device yang mengirimnya.
     
[![image.png](https://i.postimg.cc/HWQGS5mm/image.png)](https://postimg.cc/238Xy139)

    Setelah paket broadcast tersebut diterima ke semua device dalam satu jaringan maka IP yang sesuai (192.168.1.2) akan melakukan replay sementara yang IP nya tidak sesuai tidak akan melakukan replay dan akan melakukan drop pada paket tersebut yang terjadi pada Layer Network (OSI Layer - 3).


### Apakah PC0 ke PC1 terjadi broadcast lagi ?
### JAWAB->"tidak perlu menggunakan broadcast lagi"
[![image.png](https://i.postimg.cc/zf0vHMdd/image.png)](https://postimg.cc/JyHM9TCJ)

    Gambar di atas membutkikan pada ARP Cache sudah terdaftar IP Logika dan IP Physical sudah terdaftar sesuai dengan PC0 (192.168.1.1) jadi dari situ sudah tidak memerlukan broadcast.

### Apakah PC1 ke PC0 terjadi broadcast lagi ?
### JAWAB->"tidak memerlukan broadcast"
[![image.png](https://i.postimg.cc/BZD8Mhtv/image.png)](https://postimg.cc/Jtr4h5Nw)

    Gambar di atas seperti gambar pada scenario 2 jadi tidak perlu melakukan broadcast paket lagi karena sudah terdaftar pada ARP Cache.
    Karena sewaktu menerima request (ping) dari PC 0 (192.168.1.1) sudah berisi MAC / Phsyical Address dari sumbernya.