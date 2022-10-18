NAMA : Muh Khozinatul Asror
NRP : 3121600026
KELAS : 2 D4-IT-A

## Tugas minggu ke 8

## Traceroute dan Time to Live
### Time To Live

    Time To Live adalah sebuah mekanisme yang membatasi usia pakai pada suatu paket dalam komputer/jaringan. Value TTL menentukan paket harus diterukan ke router selanjutnya atau tidak yang mana TTL ini memiliki nilai default 64 dengan maksimum 255 dan nilainya akan berkurang ketika melewati router atau hop. TTL dapat dilihat ketika kita melakukan ping pada jaringan.

## TOPOLOGI Tracer Route dan Time to Live
[![image.png](https://i.postimg.cc/NMYBGbkB/image.png)](https://postimg.cc/3yLPnXqc)

### Konfigurasi IP Route
|Perangkat|Interface|IP          |
|---------|---------|------------|
|Router0  |Fa0/0    |192.168.2.2 |
|         |Fa1/0    |192.168.1.2 |
|Router1  |Fa0/0    |192.168.1.1 |
|         |Fa1/0    |192.168.3.2 |
|         |Fa2/0    |192.168.5.1 |
|Router2  |Fa0/0    |192.168.2.1 |
|         |Fa1/0    |192.168.3.1 |
|         |Fa2/0    |192.168.4.1 |

### Konfigurasi IP Mac
|Perangkat|Interface|IP          |
|---------|---------|------------|
|PC0      |Fa0/0    |192.168.4.2 |
|PC1      |Fa0/0    |192.168.5.2 |

### konfigurasi Static routing pada komputer
|Perangkat|Destination Network |Netmask       |Via         |Metric|
|---------|--------------------|--------------|------------|------|
|Router0  |192.168.4.0         |255.255.255.0 |192.168.2.1 |10 (default) |
|         |192.168.5.0         |255.255.255.0 |192.168.1.1 |10 (default) |
|Router1  |192.168.4.0         |255.255.255.0 |192.168.3.1 |10 (default) |
|         |192.168.2.0         |255.255.255.0 |192.168.1.2 |10 (default) |
|Router2  |192.168.5.0         |255.255.255.0 |192.168.3.1 |10 (default) |
|         |192.168.1.0         |255.255.255.0 |192.168.2.2 |10 (default) |

    konfigurasi static bisa dilakukan dengan cara memasukkan perintah pada CLI yitu (ip route [Destination Network][Netmask][Via][Metric])

## Latihan Percobaan
> jika menggunakan windows : tracert {IP address}
> jika menggunakan linux : traceroute {IP address}

![pc0.png](https://i.postimg.cc/dV3PRZ4S/pc0.png)]
    
    pc0 (192.168.4.2) melakukan tracert ke pc1 (192.168.5.2) melalui router 2 (192.168.4.1) lalu ke router 1 (192.168.3.2) dan akhirnya ke pc1 (192.168.5.2) dan sampai percobaan ke 3 hasil tetap sama.
[![pc1.png](https://i.postimg.cc/DyCRzynQ/pc1.png)](https://postimg.cc/RNHgsm3q)

    dan pada saya coba tracert 3 kali pada pc1 (192.168.5.2) melakukan tracert ke pc0 (192.168.4.2) melalui router 1 (192.168.5.1) lalu ke router 2 (192.168.3.1) dan akhirnya ke pc0 (192.168.4.2).
>Mengubah Metric Static Routing

|  Devices 	| Destination Network 	|    Netmask    	|     Via     	|    Metric    	|
|:--------:	|:-------------------:	|:-------------:	|:-----------:	|:------------:	|
| Router 0 	|     192.168.4.0     	| 255.255.255.0 	| 192.168.2.1 	| 10 (Default) 	|
|          	|     192.168.5.0     	| 255.255.255.0 	| 192.168.1.1 	| 10 (Default) 	|
| Router 1 	|     192.168.4.0     	| 255.255.255.0 	| 192.168.3.1 	| 10 (Default) 	|
|          	|     192.168.4.0     	| 255.255.255.0 	| 192.168.1.2 	|       1      	|
| Router 2 	|     192.168.5.0     	| 255.255.255.0 	| 192.168.3.1 	| 10 (Default) 	|
|          	|     192.168.5.0     	| 255.255.255.0 	| 192.168.2.2 	|       1      	|
    
    jalur yang paling efisien dengan mw]engubah nilai metric adalah jalur yang melalui router 1.
[![pc0test2.png](https://i.postimg.cc/7Z3s2HyQ/pc0test2.png)](https://postimg.cc/nXLG8trv)

    pc0 (192.168.4.2) tracert ke pc1 (192.168.5.2) setelah menambahkan static router yang baru dengan metric 1. Jalur yang dilalui oleh paket data tersebut adalah jalur yang melalui router 2 (192.168.4.1) lalu ke router 0 (192.168.2.2) lalu ke router1 (192.168.1.1) dan akhirnya ke pc1 (192.168.5.2).
[![pc1test2.png](https://i.postimg.cc/MZ1d4ZnZ/pc1test2.png)](https://postimg.cc/kDXQRmNL)

    pc1 (192.168.5.2) tracert ke pc0 (192.168.4.2). paket data tersebut melalui jalur yang menghubungkan router 1 (102.168.5.1) lalu ke router 0 (192.168.1.2) lalu ke router2 (192.168.2.1) dan akhirnya ke pc0 (192.168.4.2).

    dapat disimpulkan dengan adanya routing berbeda pada masing masing roter menyebabkan jalur yang dilalui oleh paket data tersebut berbeda dengan sebelumnya. Pada percobaan kali ini, jalur yang paling efisien adalah jalur yang melalui router 1. dikarenakan metric yang digunakan untuk routing yang melalui router router 1 dan 2 adalah 10 dan router 0 adalah 1.
