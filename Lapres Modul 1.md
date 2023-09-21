MODUL 1
# Soal
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

# Jawaban
## Nomor 1
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
## Nomor 2
## Nomor 3
## Nomor 4
Jawaban : Pertama cari packet nomor 130 lalu bisa checksum nya di bagian "User Data Protocol" ada Checksum: 0x18e5
![SSNo4](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/0dbe4deb-3d3f-4986-9b23-e02ebe4a6ccb)
## Nomor 5
## Nomor 6
## Nomor 7
Jawaban : Gunakan filter ``ip.dst == 184.87.193.88`` untuk mencari paket yang menuju IP 184.87.193.88.
![SSNo7](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/632e9b19-3010-4178-84b6-76ca988688e2)
## Nomor 8
Jawaban : Gunakan filter ``tcp.dstport == 80 || udp.dstport == 80`` untuk mengambil semua protokol paket yang menuju port 80!
![SSNo8](https://github.com/ZhafranMZ/Jarkom-Modul-1-F11-2023/assets/114043452/78ce7370-ec1f-4cd3-acd5-2a6a9d39091b)
## Nomor 9
## Nomor 10
