
#################################################################################################

1. Pengertian Wireless MikroTik

Wireless MikroTik = fitur jaringan nirkabel pada RouterOS.
Digunakan untuk:
Access Point (AP)
Client
Point to Point (PTP)
Point to Multi Point (PTMP)

2. Mode Wireless

Wireless dibagi menjadi beberapa mode, yaitu :
ap-bridge → Mode Access Point
station → Mode client biasa
station-bridge → Client tapi bisa bridge (PTP)
bridge → AP untuk PTP / PTMP
wds-slave / wds-master → Mode WDS (jarang dipakai sekarang)

3. Frekuensi & Band

2.4 GHz
2412 – 2484 MHz
Jangkauan jauh, tapi interferensi tinggi

5 GHz
5180 – 5825 MHz
Lebih stabil, throughput lebih besar

4. Channel Width

20 MHz → stabil, jarak jauh
40 MHz → lebih cepat, jarak menengah
80 MHz → throughput tinggi, jarak dekat

6. Security Profile

WPA2-PSK
WPA3 (di RouterOS terbaru)
AES Encryption
Disable WPS
Gunakan password kuat

7. Basic Parameter Wireless

SSID → Nama WiFi
Mode → ap-bridge / station
Band → 2GHz / 5GHz

Frequency → Channel
Channel Width
Tx Power
Country & Regulatory Domain

8. Bridge Wireless

Wireless interface harus dimasukkan ke bridge
Supaya:

Bisa dapat IP DHCP
Bisa routing & NAT

9. Konsep Link Wireless

PTP (Point to Point) → 1 AP ke 1 client
PTMP (Point to Multi Point) → 1 AP ke banyak client
Access Point → untuk user WiFi biasa

BASIC CONFIGURASI WIRELESS :

1. Setting Wireless Interface (Access Point)
Via Winbox

Wireless → wlan1
Mode : ap-bridge
SSID : WIFI-JWI
Band : 2GHz-B/G/N (atau 5GHz-A/N/AC kalau 5G)
Channel Width : 20MHz
Frequency : auto (atau isi manual, misal 2412)
Country : indonesia
Installation : indoor

Klik Apply → OK

2. Buat Security Profile (Password WiFi)

Wireless → Security Profiles → +
Name : wifi-secure
Mode : dynamic-keys
Authentication Types : WPA2-PSK
Unicast Ciphers : aes-ccm
Group Ciphers : aes-ccm
WPA2 Pre-Shared Key : passwordkuat123

Klik Apply → OK

Lalu pasang ke wlan1 → Security Profile → wifi-secure

3. Masukkan Wireless ke Bridge

Bridge → Ports → +
Interface : wlan1
Bridge : bridge1

Klik OK

(Kalau belum ada bridge1, buat dulu di menu Bridge)

4. Aktifkan DHCP Server (Biar Client Dapat IP Otomatis)

IP → DHCP Server → DHCP Setup
Interface : bridge1

Next → Next → Finish

5. NAT (Supaya Bisa Internet)

IP → Firewall → NAT → +
Chain : srcnat
Out Interface : ether1 (port ke internet)
Action : masquerade

Klik OK

#################################################################################################


BASIC CONFIGURASI VERSI TERMINAL :
/interface wireless set wlan1 mode=ap-bridge ssid=WIFI-JWI band=2ghz-b/g/n channel-width=20mhz frequency=auto country=indonesia installation=indoor

/interface wireless security-profiles add name=wifi-secure authentication-types=wpa2-psk unicast-ciphers=aes-ccm group-ciphers=aes-ccm wpa2-pre-shared-key=passwordkuat123

/interface wireless set wlan1 security-profile=wifi-secure

/interface bridge add name=bridge1
/interface bridge port add bridge=bridge1 interface=wlan1
/interface bridge port add bridge=bridge1 interface=ether2

/ip dhcp-server setup

#################################################################################################

TOPOLOGY SIMPLE :
Internet
   |
ether1 (WAN)
[MikroTik]
ether2 + wlan1 → Client WiFi


TESITNG :

Connect ke SSID WIFI-JWI

Cek:
ip address
ping 8.8.8.8

#################################################################################################
