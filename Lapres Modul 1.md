MODUL 1
# Soal
1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 
b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!
3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?
b. Protokol layer transport apa yang digunakan?
4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?
5. Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
b. Port berapakah pada server yang digunakan untuk service SMTP?
c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?
6. Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.
7. Berapa jumlah packet yang menuju IP 184.87.193.88?
8. Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)
9. Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!
10. Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

# Jawaban
## Nomor 1
Jawaban : Filter dengan query ``ftp.request.command == "STOR"``
Gambar 1:
Gambar sequence number:
a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?
jawaban : 258040667
b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
jawaban : 1044861039
Gambar sequence number:
c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
jawaban : 1044861039
d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
jawaban : 258040696
## Nomor 2
## Nomor 3
## Nomor 4
Jawaban : Pertama cari packet nomor 130 lalu bisa checksum nya di bagian "User Data Protocol" ada Checksum: 0x18e5
Gambar:
## Nomor 5
## Nomor 6
## Nomor 7
Jawaban : Gunakan filter ``ip.dst == 184.87.193.88`` untuk mencari paket yang menuju IP 184.87.193.88.
Gambar :
## Nomor 8
Jawaban : Gunakan filter ``tcp.dstport == 80 || udp.dstport == 80`` untuk mengambil semua protokol paket yang menuju port 80!
Gambar :
## Nomor 9
## Nomor 10

Algoritma untuk mengerjakan seperti berikut:
1. Download file.zip dari link ynag disediakan;
2. Unzip file.zip;
3. Print random file.jpg;
4. Buat direktori "HewanDarat", "HewanAmphibi", dan "HewanAir";
5. Pindahkan file.jpg ke dalam folder "HewanDarat", "HewanAmphibi", dan "HewanAir" sesuai dengan namanya;
6. Zip masing-masing folder.

## binatang.c
File binatang.c merupakan program untuk menjawab soal nomor 1.

1. ```binatang.c```
Berisi code berikut
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <dirent.h>
#include <sys/stat.h>
#include <sys/wait.h>
#include <unistd.h>
#include <time.h>

void download(){
	int status = system("wget -nc --content-disposition \"https://drive.google.com/uc?export=download&id=1oDgj5kSiDO0tlyS7-20uz7t20X3atwrq\"");
	if (status == 0){
		printf("File sudah ada atau berhasil diunduh\n");
	} else{
		printf("File gagal diunduh\n");
		exit(EXIT_FAILURE);
	}
}

void unzip(){
	char *zip_Name = "binatang.zip";
	char *folder_Name = "binatang.folder";
	char *unzip_args[] = {"unzip", "-d", folder_Name, zip_Name, NULL};
	pid_t pid = fork();
	if (pid == 0){
		mkdir(folder_Name, S_IRWXU | S_IRWXG | S_IRWXO);
		execv("/bin/unzip", unzip_args);
		perror("execv");
		exit(EXIT_FAILURE);
	} else if (pid > 0){
		wait(NULL);
		printf("Unzip berhasil  dilakukan\n");
	} else{
		perror("fork");
		exit(EXIT_FAILURE);
	}
}

void zip(){
	char *folders[3] = {"HewanDarat", "HewanAmphibi", "HewanAir"};
	char zip_Name[128];
	char cmd[128];
	int i;
	for(i = 0; i < 3; i++){
		snprintf(cmd, sizeof(cmd), "rm -r %s", folders[i]);
		snprintf(zip_Name, sizeof(zip_Name), "%s.zip", folders[i]);
		char *zip_args[] = {"zip", "-r", zip_Name, folders[i], NULL};
		int pid = fork();
		if (pid == 0){
			execv("/bin/zip", zip_args);
			perror("execv");
			exit(EXIT_FAILURE);
		} else if (pid > 0){
			wait(NULL);
			printf("Zip folder %s berhasil dilakukan\n", folders[i]);
		} else {
			perror("fork");
			exit(EXIT_FAILURE);
		}
		system(cmd);	
	}
}

void makeDir(){
	char dirDir[256];
	char *dirs_name[3] = {"HewanDarat", "HewanAmphibi", "HewanAir"};
	int i;
	for (i = 0; i < 3; i++){
		snprintf(dirDir, sizeof(dirDir), "%s", dirs_name[i]);
		int status = mkdir(dirDir, S_IRWXU | S_IRWXG | S_IRWXO);
		if (status == -1){
			perror("mkdir");
			exit(EXIT_FAILURE);
		}
		printf("Direktori %s berhasil dibuat\n", dirs_name[i]);
	}
}

void moveAndRand(){
	char *dirHab;
	char *folder_Name = "binatang.folder";
	char cmd[1024];
	DIR *dir;
	struct dirent *ent;
	char filenames[128][128];
	int count = 0;

	if ((dir = opendir(folder_Name)) != NULL){
		while ((ent = readdir(dir)) != NULL){
			if (strstr(ent->d_name, ".jpg")){
				char *name = strtok(ent->d_name, ".");
				if (strstr(name, "amphibi")){
					dirHab = "HewanAmphibi";
				} else if (strstr(name, "darat")){
					dirHab = "HewanDarat";
				} else if (strstr(name, "air")){
					dirHab = "HewanAir";
				}
				strncpy(filenames[count], name, 128);
				count++;
				sprintf(cmd, "mv %s/%s.jpg %s/", folder_Name, ent->d_name, dirHab);
				system(cmd);
			}
		}
		closedir(dir);
	} else{
		perror("Gagal untuk membuka directory");
		exit(EXIT_FAILURE);
	}
	
	if (count > 0){
		srand(time(NULL));
		int randomize = rand() % count;
		printf("\n%s\n\n", filenames[randomize]);
	}
	
	sprintf(cmd, "rm -r %s", folder_Name);
	system(cmd);
}

int main(){
	download();
	unzip();
	makeDir();
	moveAndRand();
	zip();
	return 0;
}
```
### main()
```c
int main(){
	download();
	unzip();
	makeDir();
	moveAndRand();
	zip();
	return 0;
}
```
Berfungsi untuk menjalankan fungsi-fungsi yang dibutuhkan umtuk menyelesaikan masalah.

#### download()
```c
void download(){
	int status = system("wget -nc --content-disposition \"https://drive.google.com/uc?export=download&id=1oDgj5kSiDO0tlyS7-20uz7t20X3atwrq\"");
	if (status == 0){
		printf("File sudah ada atau berhasil diunduh\n");
	} else{
		printf("File gagal diunduh\n");
		exit(EXIT_FAILURE);
	}
}
```
- download() berfungsi untuk mendownload file zip melalui link yang diberikan dengan menggunakan system(wget);
- -nc berfungsi untuk mengecek apakah file yang akan didownload sudah ada di directory atau belum. Jika belum maka akan mendownload, jika sudah maka tidak perlu mendownload;
- --content-disposition digunakan untuk menjamin bahwa link yang dipakai untuk mendownload tidak berubah;
- Status digunakan untuk memberitahu apakah proses download berhasil atau tidak;
- Status juga memudahkan debugging.

#### unzip()
```c
void unzip(){
	char *zip_Name = "binatang.zip";
	char *folder_Name = "binatang.folder";
	char *unzip_args[] = {"unzip", "-d", folder_Name, zip_Name, NULL};
	pid_t pid = fork();
	if (pid == 0){
		mkdir(folder_Name, S_IRWXU | S_IRWXG | S_IRWXO);
		execv("/bin/unzip", unzip_args);
		perror("execv");
		exit(EXIT_FAILURE);
	} else if (pid > 0){
		wait(NULL);
		printf("Unzip berhasil  dilakukan\n");
	} else{
		perror("fork");
		exit(EXIT_FAILURE);
	}
}
```
- unzip() berfungsi untuk mengunzip file zip yang di download pada fungsi download();
- Buat fork;
- Buat folder sementara "binatang.folder" untuk menyimpan hasil dari unzip supaya tidak tercampur dengan file lain dengan menggunakan mkdir;
- Unzip binatang.zip dengan execv.

#### makeDir()
```c
void makeDir(){
	char dirDir[256];
	char *dirs_name[3] = {"HewanDarat", "HewanAmphibi", "HewanAir"};
	int i;
	for (i = 0; i < 3; i++){
		snprintf(dirDir, sizeof(dirDir), "%s", dirs_name[i]);
		int status = mkdir(dirDir, S_IRWXU | S_IRWXG | S_IRWXO);
		if (status == -1){
			perror("mkdir");
			exit(EXIT_FAILURE);
		}
		printf("Direktori %s berhasil dibuat\n", dirs_name[i]);
	}
}
```
- makeDir() berfungsi untuk membuat directory baru yang nanti akan digunakan untuk menyimpan file jpg dari zip sesuai dengan habitatnya;
- Buat folder "HewanDarat", "HewanAmphibi", dan "HewanAir" dengan menggunakan mkdir dengan akses 0777;
- Status digunakan untuk memberitahu apakah proses membuat folder berhasil atau tidak;
- Status juga memudahkan debugging.


#### moveAndRand()
```c
void moveAndRand(){
	char *dirHab;
	char *folder_Name = "binatang.folder";
	char cmd[1024];
	DIR *dir;
	struct dirent *ent;
	char filenames[128][128];
	int count = 0;

	if ((dir = opendir(folder_Name)) != NULL){
		while ((ent = readdir(dir)) != NULL){
			if (strstr(ent->d_name, ".jpg")){
				char *name = strtok(ent->d_name, ".");
				if (strstr(name, "amphibi")){
					dirHab = "HewanAmphibi";
				} else if (strstr(name, "darat")){
					dirHab = "HewanDarat";
				} else if (strstr(name, "air")){
					dirHab = "HewanAir";
				}
				strncpy(filenames[count], name, 128);
				count++;
				sprintf(cmd, "mv %s/%s.jpg %s/", folder_Name, ent->d_name, dirHab);
				system(cmd);
			}
		}
		closedir(dir);
	} else{
		perror("Gagal untuk membuka directory");
		exit(EXIT_FAILURE);
	}
	
	if (count > 0){
		srand(time(NULL));
		int randomize = rand() % count;
		printf("\n%s\n\n", filenames[randomize]);
	}
	
	sprintf(cmd, "rm -r %s", folder_Name);
	system(cmd);
}
```
- moveAndRand() berfungsi untuk memindahkan file.jpg yang ada di dalam folder sementara binatang.folder ke folder "HewanDarat", "HewanAmphibi", dan "HewanAir" sesuai dengan habitatnya lalu mengeprint secara acak file.jpg yang ada.
- Masuk ke folder binatang.folder lalu cek apakah ada isinya atau tidak.
- file.jpg akan dicek satu-satu dengan strtok apakah masuk ke amphibi, darat, atau air.
- File yang sudah dicek akan dimasukkan ke dalam filenames[128][128].
- File yang sudah dicek akan dimasukkan ke folder "HewanDarat", "HewanAmphibi", dan "HewanAir" sesuai dengan habitatnya menggunakan system(cmd) yang di mana cmd berisi perintah mv.
- Print acak nama file.jpg yang tersimpan di filenames[128][128] dengan menggunakan rand().

#### zip()
```c
void zip(){
	char *folders[3] = {"HewanDarat", "HewanAmphibi", "HewanAir"};
	char zip_Name[128];
	char cmd[128];
	int i;
	for(i = 0; i < 3; i++){
		snprintf(cmd, sizeof(cmd), "rm -r %s", folders[i]);
		snprintf(zip_Name, sizeof(zip_Name), "%s.zip", folders[i]);
		char *zip_args[] = {"zip", "-r", zip_Name, folders[i], NULL};
		int pid = fork();
		if (pid == 0){
			execv("/bin/zip", zip_args);
			perror("execv");
			exit(EXIT_FAILURE);
		} else if (pid > 0){
			wait(NULL);
			printf("Zip folder %s berhasil dilakukan\n", folders[i]);
		} else {
			perror("fork");
			exit(EXIT_FAILURE);
		}
		system(cmd);	
	}
}
```
- zip() berfungsi untuk mengzip folder "HewanDarat", "HewanAmphibi", dan "HewanAir";
- Buat fork;
- Unzip binatang.zip dengan execv.

Program selesai dijalankan.

## Output
Berikut adalah output dari program di atas:
- Output Hasil Program yang berupa 3 file zip "HewanDarat.zip", "HewanAmphibi.zip", dan "HewanAir.zip"
![SS Hasil Zip](https://user-images.githubusercontent.com/114043452/230730979-d3d5f78f-b053-4f36-8a85-4220fe06b0d8.png)

- Output terminal dari program
![SS Output Terminal](https://user-images.githubusercontent.com/114043452/230730986-da3b0c50-fe32-4745-ae64-e0f843c8fb9b.png)

- Output Isi dari masing-masing zip
![SS Zip](https://user-images.githubusercontent.com/114043452/230730993-f7eb025c-3b95-4d2f-a75c-27314a4c6c65.png)
![SS Zip isi](https://user-images.githubusercontent.com/114043452/230730991-6b0be7df-fddf-4b39-94de-25ae202c564b.png)
