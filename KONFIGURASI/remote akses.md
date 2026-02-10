CARA REMOT MIKROTIK DENGAN MENGGUNAKAN PERANGKAT WINGBOX

LANGKAH PERTAMA :
1. Sambungkan kabel LAN dari router ke laptop/pc tergantung port yang terhubung contoh :
- ether1 pada router > laptop
- lalu pilih menu IP > Service, lalu kalian pilih layanan yang akan digunakan untuk remote jarak jauh, yaitu :
API,API-SSL,FTP,Telnet,Winbox,WWW,WWW,SSL

LANGKAH KEDUA :
note : yang akan digunakan remote WinBox

2. Klik 2x pada menu Winbox
   secara default port yang digunakan Winbox adalah 8291, 
   untuk itu kalian bisa  merubah port sesuai yang kalian gunakan contoh : 800
   lalu klik APPLY > OK

LANGKAH KETIGA :
note : untuk melakukan remote router atau memanggil router dengan jaringan lain 
caranya login ulang dengan ip yang sama tapi menggunakan port yang sudah dibuat tadi

3. Buka Winbox lalu masukan ip public yang terpasang di router, 
   ip public yang terpasang adalah 22.227.14.137 cuma bedanya diakhir tambahkan port yang sudah dibuat tadi yaitu :
   22.227.14.137:800

LANGKAH KEEMPAT :

4. Cara remote Mikrotik dengan mengunakan WWW, secara default port yang digunakan oleh layanan WWW adalah 80, 
maka jika kalian ingin melakukan remote WWW, silahkan buka browser lalu ketik angka yang tadi yaitu 22.227.14.137:80

LANGKAH KELIMA :

5. Cara remote WWW-SSL,TLS,HTTPS. Setting jarak jauh Mikrotik menggunakan jaringan aman terenkripsi SSL (Secure Sockets Layer) atau 
   menggunakan TLS (Transport Layer Security) memang sangat disarankan sebagai alat salah satu solusi untuk
   menghindari serangan dari HACKER.

   penggunaan protocol jaringan TLS/SSL, selanjutnya merujuk pada istilah HTTPS yang berfungsi  untuk mengamankan komunikasi digital antara browser dan 
   website/situs sehingga data user akan lebih aman data user akan lebih aman dari pencurian data oleh pihak lain

   Cara remote Mikrotik jarak jauh dengan SSH dan Telnet.
   Selanjutnya jika anda ingin melakukan remote Mikrotik dengan SSH atau Telnet, maka membutuhkan Aplikasi/Software PuTTy.
   Kemudian agar dapat meremote Mikrotik dari jauh menggunakan SSH dan Telnet, maka terlebih dahulu silahkan rubah port sesuai yang kalian inginkan pada menu SSH dan Telnet.
   Lalu silahkan buka PuTTy lalu pilih SSH jika ingin menggunakan SSH dan pilih Telnet jika ingin menggunakan Telnet
