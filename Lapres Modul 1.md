# MODUL 1
## Anggota
- Muhammad Zhafran (5025211100)
- Mohamad Valdi Ananda Tauhid (5025221238)
## Soal
1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
- Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?
- Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?
- Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
- Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!
3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
- Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?
- Protokol layer transport apa yang digunakan?
4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?
5. Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
- Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
- Port berapakah pada server yang digunakan untuk service SMTP?
- Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?
6. Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.
7. Berapa jumlah packet yang menuju IP 184.87.193.88?
8. Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)
9. Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!
10. Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

## Jawaban
### Nomor 1
Jawaban : Filter dengan query ``ftp.request.command == "STOR"``
![SSNo1Part1](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/51967be8-9b45-4e14-876a-513cfe4a6dfe)
![SSNo1Part2](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/0baec3a2-2993-4baa-af2a-52405df04791)
- Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?
jawaban : 258040667
- Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
jawaban : 1044861039
![SSNo1Part3](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/a2d97f32-5e01-4675-b4b4-1a829716688b)
- Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
jawaban : 1044861039
- Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
jawaban : 258040696
### Nomor 2
Untuk mempermudah pencarian, masukkan filter di display filter `http && (ip.src == 10.21.78.111 || ip.dst == 10.21.78.111)` untuk memfilter semua protokol http dengan source atau destination ip portal praktikum jaringan.
Pilih salah satu paket yang tercapture, kemudian ketik "Follow" dan ketik "HTTP Stream".

![Screenshot from 2023-09-21 16-47-46](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/d76ba10b-606d-4417-b86c-afc34b0f336e)

Kita akan bisa lihat request dan response dalam protokol http. Dalam header response dari server, bisa dilihat `Server: gunicorn` itu adalah hostname server praktikum.

![Screenshot from 2023-09-21 16-48-16](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/48d5d9ff-cf10-40fe-b8ee-81e67eda743b)

Jawaban : gunicorn

### Nomor 3
Setelah membuka file pcap di wireshark beri display filter `ip.dst == 239.255.255.250 && (udp.port == 3702 || tcp.port == 3702)`. Filter itu berguna untuk memfilter tujuan ip ke 239.255.255.250 serta dengan port 3702. Setelah itu, bisa dilihat di status bar bawah di bagian kanan ada tulisan “Displayed: 21”. Berarti paket yang lolos dari display capture yang telah dimasukkan berjumlah 21.

![Screenshot from 2023-09-21 16-50-35](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/165284f5-7f72-40c7-9da7-0bf79336db7e)

Jika kita mengetik salah satu packet yang tercapture, dan kita lihat di packet details panel, kita bisa lihat di bawah “Internet Protocol Version 4” kita bisa melihat “User Datagram Protocol”. Berarti paket menggunakan protokol User Datagram Protocol atau UDP.

![Screenshot from 2023-09-21 16-51-41](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/324f4e6b-1e98-4ae0-b08b-44bd54dea6d2)

- Berapa banyak paket yang tercapture dengan IP source maupun destination address 239.255.255.250 dengan port 3702?
Jawaban : 21
- Protokol layer transport apa yang digunakan?
Jawban : UDP

### Nomor 4
Jawaban : Pertama cari packet nomor 130 lalu bisa checksum nya di bagian "User Data Protocol" ada Checksum: 0x18e5
![SSNo4](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/0dbe4deb-3d3f-4986-9b23-e02ebe4a6ccb)
### Nomor 5
Setelah membuka file pcap, beri display filter “SMTP”, untuk melihat semua paket protokol SMTP. Jika kita ketik salah satu paket, ketik “Follow” dan ketik “TCP Stream”, Kita bisa melihat pesan yang di transaksi dengan SMTP.

![Screenshot from 2023-09-21 16-53-07](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/9dcf9315-e405-43da-a4bc-1f18033af85b)

Jika kita scroll ke bawah kita bisa lihat pesan SMTP yaitu sebuah password yang di encode dengan base64.

![Screenshot from 2023-09-21 16-54-00](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/a71a6a9e-e757-4442-bcb7-171dade3240c)


Jika kita decode dengan base64, maka kita akan dapat password “5implePas5word”

![Screenshot from 2023-09-21 16-57-45](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/32c3d31b-b24b-4067-a664-6b42e52ecf2d)

Jawaban : 5implePas5word

### Nomor 6
### Nomor 7
Jawaban : Gunakan filter ``ip.dst == 184.87.193.88`` untuk mencari paket yang menuju IP 184.87.193.88.
![SSNo7](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/632e9b19-3010-4178-84b6-76ca988688e2)
### Nomor 8
Jawaban : Gunakan filter ``tcp.dstport == 80 || udp.dstport == 80`` untuk mengambil semua protokol paket yang menuju port 80!
![SSNo8](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/78ce7370-ec1f-4cd3-acd5-2a6a9d39091b)
### Nomor 9
Kita pertama butuh memberi display filter sumber ip dengan `ip.src == 10.51.40.1` kemudian buang yang destinasi ip dengan `ip.dst != 10.39.55.34`. Kemudian gabungkan kedua filter tersebut dengan operator && sehingga menjadi  `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`.

### Nomor 10
Setelah membuka file pcap, kita bisa kita beri display filter “telnet” untuk memfilter semua paket dengan protokol telnet. Ketik kanan salah satu paket dan ketik “Follow” dan ketik “TCP Stream”. 

![Screenshot from 2023-09-21 17-07-53](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/b2802729-112e-4305-b479-65f081483bbb)

Setelah itu di kanan bawah, scroll Stream sampai ketemu pesan dimana login berhasil. 

![Screenshot from 2023-09-21 17-08-07](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/63389207/25c4525a-00f9-4745-a93a-5abd75eab71a)

Bisa di lihat di paling atas pesan bahwa username adalah “ddhhaaffiinn” karena setiap ketik text maka console akan berubah, maka setiap dua karakter, ubah menjadi satu menjadi “dhafin”. Kemudian untuk password bisa dilihat di bawah yaitu “kesayangannyak0k0”.

Jawaban : dhafin:kesayangannyak0k0













