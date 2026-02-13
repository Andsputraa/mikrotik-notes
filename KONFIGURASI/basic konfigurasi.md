MACAM MACAM BASIC KONFIGURASI MIKROTIK, SEBAGAI BERIKUT :

/system identity set name=RTR-JWI-01

/system clock set time-zone-name=Asia/Jakarta

/system ntp client set enabled=yes server-dns-names=id.pool.ntp.org

/interface print
/interface set ether1 name=WAN
/interface set ether2 name=LAN

/ip address add address=192.168.1.1/24 interface=LAN comment=LAN
/ip route add dst-address=0.0.0.0/0 gateway=192.168.1.254
/ip dns set servers=8.8.8.8,1.1.1.1 allow-remote-requests=yes
/ip pool add name=pool-lan ranges=192.168.1.10-192.168.1.200

/ip dhcp-server add name=dhcp-lan interface=LAN address-pool=pool-lan disabled=no
/ip dhcp-server network add address=192.168.1.0/24 gateway=192.168.1.1 dns-server=8.8.8.8
/ip firewall filter

add chain=input connection-state=established,related action=accept
add chain=input connection-state=invalid action=drop
add chain=input protocol=icmp action=accept
add chain=input in-interface=WAN action=drop

/user add name=noc group=full password=xxxxxxx
