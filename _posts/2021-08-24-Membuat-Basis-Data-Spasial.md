## Membuat Basis Data Spasial dengan PostgreSQL
Kali ini kita akan mencoba membuat basis data spasial dengan postgreSQL. Kita akan gunakan pgAdmin4 karena tampilan grafisnya mudah dipahami. Buat basis data baru dengan klik kanan pada server lalu klik Create > Database

![image](https://user-images.githubusercontent.com/43196730/130584948-8e731fc0-bec4-4913-bcf1-9c35335148a8.png)

Kita akan beri nama database dengan nama poi

![image](https://user-images.githubusercontent.com/43196730/130585467-5bd2685d-324c-4ed7-a0b5-8327bcb30dc5.png)

Klik pada icon query tools untuk menjalankan perintah query pada basis data

![image](https://user-images.githubusercontent.com/43196730/130585892-28274f2c-8632-4c21-951f-c3ce2579e84b.png)

Ketik seperti di bawah ini untuk menyalakan ekstensi postgis pada database:
```
CREATE EXTENSION postgis;
```
Klik run atau gunakan tombol F5
Untuk cek kembali apakah postgis sudah dinyalakan bisa dengan perintah ini:
```
SELECT postgis_full_version();
```
### Import Shapefile
Anda dapat menggunakan perintah berikut ini untuk import data format shapefile ke dalam database. Di sini kita menggunakan ogr2ogr pada sistem operasi Linux.
```
export PGPASSWORD=mydatabasepassword
ogr2ogr -f "PostgreSQL" PG:"dbname=poi user=postgres" -nlt PGEOMETRY /path/to/file.shp
```
Anda dapat melihat tabel yang baru saja dibuat pada Schemas > Public > Tables
Klik kanan dan tampilkan data. Anda dapat melihat keseluruhan tabel

![image](https://user-images.githubusercontent.com/43196730/130587682-9dc64f67-2fbd-4bca-8cea-f25692fc43f8.png)
























