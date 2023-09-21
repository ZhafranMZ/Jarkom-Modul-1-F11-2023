MODUL 1
# Soal
1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.\n
a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? \n
b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?\n 
c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?\n
d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?\n
2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!\n
3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:\n
a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?\n
b. Protokol layer transport apa yang digunakan?\n
4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?\n
5. Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.\n
a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?\n
b. Port berapakah pada server yang digunakan untuk service SMTP?\n
c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?\n
6. Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.\n
7. Berapa jumlah packet yang menuju IP 184.87.193.88?\n
8. Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)\n
9. Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!\n
10. Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet\n

# Jawaban
## Nomor 1
Jawaban : Filter dengan query ``ftp.request.command == "STOR"``\n
Gambar 1:
Gambar sequence number:
a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?\n
jawaban : 258040667\n
b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? \n
jawaban : 1044861039\n
Gambar sequence number:
c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?\n
jawaban : 1044861039\n
d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?\n
jawaban : 258040696\n
## Nomor 2
## Nomor 3
## Nomor 4
Jawaban : Pertama cari packet nomor 130 lalu bisa checksum nya di bagian "User Data Protocol" ada Checksum: 0x18e5\n
Gambar:
## Nomor 5
## Nomor 6
## Nomor 7
Jawaban : Gunakan filter ``ip.dst == 184.87.193.88`` untuk mencari paket yang menuju IP 184.87.193.88.\n
Gambar :
## Nomor 8
Jawaban : Gunakan filter ``tcp.dstport == 80 || udp.dstport == 80`` untuk mengambil semua protokol paket yang menuju port 80!\n
Gambar :
## Nomor 9
## Nomor 10

## Output
Berikut adalah output dari program di atas:
- Output Hasil Program yang berupa 3 file zip "HewanDarat.zip", "HewanAmphibi.zip", dan "HewanAir.zip"
![SS Hasil Zip](https://user-images.githubusercontent.com/114043452/230730979-d3d5f78f-b053-4f36-8a85-4220fe06b0d8.png)

- Output terminal dari program
![SS Output Terminal](https://user-images.githubusercontent.com/114043452/230730986-da3b0c50-fe32-4745-ae64-e0f843c8fb9b.png)

- Output Isi dari masing-masing zip
![SS Zip](https://user-images.githubusercontent.com/114043452/230730993-f7eb025c-3b95-4d2f-a75c-27314a4c6c65.png)
![SS Zip isi](https://user-images.githubusercontent.com/114043452/230730991-6b0be7df-fddf-4b39-94de-25ae202c564b.png)
