NAMA : Muh Khozinatul Asror
NRP : 3121600026
KELAS : 2 D4-IT-A

# Tugas minggu ke 2
# Documentation Task Wireshark
## Colors Rule

Wireshark menggunakan warna untuk membantu mengidentifikasi jenis lalu lintas secara sekilas. Secara default, hijau adalah lalu lintas TCP, biru tua adalah lalu lintas DNS, biru muda adalah lalu lintas UDP, dan hitam mengidentifikasi paket TCP dengan masalah — misalnya, mereka bisa saja dikirim tidak sesuai pesanan.
| Color in Wireshark | Packet Type |
|:------------------:|:----------------------------------------------------------------------------:|
| Light purple | TCP |
| Light blue | UDP |
| Black | Packets with errors |
| Light green | HTTP traffic |
| Light yellow | Windows-specific traffic, including Server Message Blocks (SMB) and NetBIOS |
| Dark yellow | Routing |
| Dark gray | TCP SYN, FIN and ACK traffic |
| Red | Invalid Display Filter |

## Check IP Address | Default Gateway | Ping-it
[![no1.png](https://i.postimg.cc/TYpNBPct/no1.png)](https://postimg.cc/xcVPznhm)
Dapat kita ketahui bahwa ip pada laptop saya yakni 192.168.18.27 (enp4s0 / ethernet) dan default gatewaynya 192.168.18.1 dengan menggunakan ping pada default gateway yang diberikan oleh router (enp4s0 / ethernet) sudah bisa melakukan analisa suatu packet dengan bantuan Wireshark.

## Packet Analyzer
[![no2.png](https://i.postimg.cc/tCNdSQKB/no2.png)](https://postimg.cc/QHVWCPx7)
Gambar di atas menunjukkan bahwa IP Address pada adaptor enp4s0 / ethernet yakni 192.168.18.27 dan default gatewaynya 192.168.18.1 dengan data tersebut kita bisa mengetahui packet yang terlintas pada Wireshark.

### Detail Packet Analyzer Frame
[![no3.png](https://i.postimg.cc/t4PKmzdq/no3.png)](https://postimg.cc/QF8YF1nw)
Dalam box frame terdapat:
- Arrival Time: Sep 6, 2022 11:41:25.541810000 Asia Standard Time
Menunjukkan waktu saat pengiriman data
- [Time shift for this packet: 0.000000000 seconds]
Epoch Time: 1662439285.541810000 seconds
[Time delta from previous captured frame: 1.440846000 seconds]
[Time delta from previous displayed frame: 1.440846000 seconds]
[Time since reference or first frame: 4.425713000 seconds]
Menunjukkan waktu sebelum capture dari frame, yaitu 1.440846000 seconds, waktu setelah frame ditampilkan yaitu 1.440846000 seconds, dan waktu sejak awal frame 4.425713000 seconds.
- Frame Number: 15
Menunjukkan nomor dari frame tersebut yaitu 15.
- Frame Length: 72 bytes (592 bits)
Menunjukkan panjangnya frame adalah sebasar 72 bytes.
- [Protocols in frame: eth:ethertype:ip:icmp:data]
Menunjukkan protokol-protokol apa saja yang ada di frame 15 yaitu
ada Ethernet, Internet Protocol (IP), Internet Control Message Protocol
(ICMP) & Data.
- Kesimpulan:
Lapisan ini menunjukkan apa saja yang ada dalam satu frame yaitu seperti protokol-protokol yang ada di lapisan ini Ethernet, Internet Protocol (IP), Transmission Control Protocol (TCP), Hypertext Transfer Protocol (HTTP), dan data-text-lines.

### Detail Packet Analyzer Ethernet II
[![no5.png](https://i.postimg.cc/L5Kfv2m6/no5.png)](https://postimg.cc/gXsn29wf)
Dalam box Ethernet II terdapat:
- Source: LiteonTe_72:6f:1b (74:4c:a1:72:6f:1b), Destination: HuaweiTe_02:6c:50 (c0:bc:9a:02:6c:50)
Menunjukkan MAC dari source yaitu LiteonTe_72:6f:1b (74:4c:a1:72:6f:1b) dan MAC dari destination HuaweiTe_02:6c:50 (c0:bc:9a:02:6c:50).
- Kesimpulan:
Lapisan data link MAC dari source yaitu LiteonTe_72:6f:1b (74:4c:a1:72:6f:1b) dan MAC dari HuaweiTe_02:6c:50 (c0:bc:9a:02:6c:50).

### Detail Packet Analyzer IPV4
[![no4.png](https://i.postimg.cc/3xFkQ2Yh/no4.png)](https://postimg.cc/9DzmGRDg)
Dalam box Internet Protocol terdapat:
- 0100 .... = Version: 4
Menunjukkan IP versi yang digunakan adalah versi 4
- .... 0101 = Header Length: 20 bytes (5)
Menunjukkan panjangnya header yang ada di lapisan network adalah sebesar 20 bytes
- InternetSrc: 192.168.18.27, Dst: 192.168.18.1
Menunjukkan IP dari source yaitu 192.168.18.27 dan IP dari destination
yaitu 192.168.18.1
- Kesimpulan:
Lapisan network, panjangnya header yang diberikan sebesar 20 bytes
dengan IP source 192.168.18.27 dan IP destination yaitu 192.168.18.1

### Detail Protcol ICMP
[![no6.png](https://i.postimg.cc/BQV0L6pF/no6.png)](https://postimg.cc/ZCpgXJ1Y)
- Type: 8 (Echo (ping) request)
- Code: 0
- Checksum: 0x4340 [correct]
- Identifier (BE): 1 (0x0001)
- Identifier (LE): 256 (0x0100)
- Sequence Number (BE): 2587 (0x0a1b)
- Sequence Number (LE): 6922 (0x1b0a)
- [Response frame: 16]
Dari data ICMP di atas saat echo ping request tersebut, icmp bertype 8, code 0, dengan
algoritma checksum 0x4340, banyak identifier (ident ifikasi) 256 bytes dan Sequence
number 6922 byte. Serta hasil diatas menunjukkan saat proses request ping, paket
dari source (192.168.18.27) IP address dari komputer kita akan merequest ({echo (ping)
request) ke destinat ion (192.168.18.1) IP address router wifi biznet.
