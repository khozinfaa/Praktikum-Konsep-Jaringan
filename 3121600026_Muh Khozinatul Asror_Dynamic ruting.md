## Tugas Minggu KE (9)

## Nama : Muh Khozinatul Asror
## Kelas : 2 D4-IT-A
## NRP : 3121600026

# ROUTING DYNAMIC


**APA ITU Dynamic Routing**
1. Router mengirimkan routing table ke semua router yang terhubung pada jaringan.
2. Router yang menerima routing table akan melakukan update routing table sesuai dengan routing table yang diterima.
3. Setelah update routing table, router akan mengirimkan routing table yang sudah diupdate ke semua router yang terhubung pada jaringan.
4. Langkah 2 dan 3 akan terus berulang sampai semua router pada jaringan memiliki routing table yang sama.



**APA ITU Routing Information Protocol (RIP)**

RIP adalah suatu routing protocol yang digunakan untuk melakukan routing pada jaringan IP. RIP menggunakan metode distance vector untuk menentukan rute ke suatu jaringan.

Metode distance vector ini adalah metode routing yang menggunakan vektor jarak untuk menentukan rute ke suatu jaringan. Vektor jarak ini merupakan jarak dari router ke suatu jaringan. Vektor jarak ini disebut dengan hop count. Hop count adalah jumlah router yang dilewati untuk menuju suatu jaringan.

RIP juga menggunakan metode broadcast untuk melakukan update routing table dan metode split horizon untuk menghindari routing loop. Cara kerja RIP yaitu dengan menghitung jarak dari router ke suatu jaringan dengan cara menghitung jumlah router yang dilewati untuk menuju suatu jaringan. Jika router yang dilewati lebih sedikit, maka jaraknya akan lebih dekat. Jarak yang lebih dekat akan lebih diutamakan untuk forwarding suatu paket daripada jarak yang lebih jauh.

**BAGAIMANA CARA KERJA RIP**
Host mendengar pada alamat broadcast jika ada update routing dari gateway. Host akan memeriksa terlebih dahulu routing table lokal jika menerima update routing . Jika rute belum ada, informasi segera dimasukkan ke routing table .

# PRAKTIKUM TRACE ROUTE dan TTL

**TOPOLOGI YANG DIGUNAKAN**

[![topologi.png](https://i.postimg.cc/BQsW0N8w/topologi.png)](https://postimg.cc/PN6VbWQm)

Pada topologi diatas masih menggunakan topologi yang lama dimana terdiri dari 3 buah router, 2 buah PC, dan 2 buah switch. Jenis router yang digunakan adalah Router-PT yang dimodifikasi portnya sesuai kebutuhan.

**Konfigurasi IP Route**
|  Devices 	| Interface 	|      IP     	|
|:--------:	|:---------:	|:-----------:	|
| Router 0 	|   Fa0/0   	| 192.168.2.2 	|
|          	|   Fa1/0   	| 192.168.1.2 	|
| Router 1 	|   Fa0/0   	| 192.168.1.1 	|
|          	|   Fa1/0   	| 192.168.3.2 	|
|           |   Fa2/0   	| 192.168.5.1   |
| Router 2 	|   Fa0/0   	| 192.168.2.1 	|
|          	|   Fa1/0   	| 192.168.3.1 	|
|           |   Fa2/0   	| 192.168.4.1   |

**Konfigurasi IP PC**
|  Devices 	| Interface 	|      IP     	|
|:--------:	|:---------:	|:-----------:	|
|    PC0   	|   Fa0/0   	| 192.168.4.2 	|
|    PC1   	|   Fa0/0   	| 192.168.5.2 	|

**Konfigurasi Routing Dengan RIP**
|  Devices 	| Destination Network 	
|:--------:	|:-------------------:		
| Router 0 	|     192.168.1.0     	
|          	|     192.168.2.0     
| Router 1 	|     192.168.1.0     
|          	|     192.168.3.0     
| Router 2 	|     192.168.2.0     
|          	|     192.168.3.0  
|          	|     192.168.4.0  

Dalam konfigurasi Dynamic routing diatas dengan RIP, dapat dilakukan dengan cara memasukkan perintah pada CLI. 

        Router(config)#router rip
        Router(config-router)#network 192.168.1.0
        Router(config-router)#network 192.168.2.0

**Convergent Dan Test**
 [![convergent.png](https://i.postimg.cc/9f1Scj7x/convergent.png)](https://postimg.cc/JyDKQvKJ)
 
 Konvergensi adalah keadaan satu set router yang memiliki informasi topologi yang sama tentang internetwork di mana mereka beroperasi. Untuk satu set router telah konvergen , mereka harus telah mengumpulkan semua informasi topologi yang tersedia dari satu sama lain melalui protokol routing yang diimplementasikan , informasi yang mereka kumpulkan tidak boleh bertentangan dengan informasi topologi router lain di set, dan itu harus mencerminkan keadaan sebenarnya dari jaringan. Dengan kata lain: dalam jaringan konvergensi semua router "setuju" seperti apa topologi jaringan itu.

Konvergensi merupakan gagasan penting untuk satu set router yang terlibat dalam routing dinamis . Semua Protokol Gateway Interior mengandalkan konvergensi agar berfungsi dengan baik. Untuk konvergen itu adalah keadaan normal dari sistem otonom operasional . Exterior Gateway Routing Protocol BGP biasanya tidak pernah konvergen karena Internet terlalu besar untuk perubahan yang dapat dikomunikasikan dengan cukup cepat.

Terlihat pada percobaan di atas bahwa paket yang dikirimkan dari PC0 ke PC1 adalah sebagai berikut:

1. PC0 mengirimkan paket ke router 1.
2. Router 2 menerima paket dan mengirimkan paket ke router 1.
3. Router 2 menerima paket dan mengirimkan paket ke PC1.
4. PC1 menerima paket.

Tracert di atas ialah percobaan yang pertama kali jadi belum ada routing table yang ada di router 2. Routing table akan terupdate setelah router 2 menerima routing table dari router 1. Terdapat jeda waktu disana karena routing table belum terupdate maka dari itu sistem convergent di mulai pada saat routing table masih belum terbentuk.




