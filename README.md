# EtherChannel_DHCP_OSPF
topologi jaringan yang memanfaatkan EtherChannel untuk agregasi link, DHCP untuk pengalokasian IP otomatis, dan OSPF untuk routing dinamis. 

##  EtherChannel (Agregasi Link)
Link Aggregation Control Protocol (LACP) digunakan untuk menggabungkan beberapa link fisik antar switch menjadi satu link logis (Port-Channel).

Switch yang dihubungkan dengan EtherChannel:
SW112 ↔ SW1 dan SW211 ↔ SW212

Manfaat:
Meningkatkan kapasitas bandwidth antar switch.
Redundansi: Jika salah satu link fisik gagal, Port-Channel tetap aktif.

## Konfigurasi DHCP
Dynamic Host Configuration Protocol (DHCP) diaktifkan pada kedua router untuk memberikan alokasi IP otomatis ke perangkat dalam jaringan.

Router R1:
1. Subnet 172.16.1.0/24: DHCP melayani perangkat seperti PC0, Laptop1, dan DNS Server.
2. Subnet 172.16.2.0/24: DHCP menyediakan IP untuk perangkat di subnet lain.
   
Router R2:
1. Subnet 192.168.1.0/24: DHCP melayani perangkat seperti PC2, Server 1, dan Laptop2.
2. Subnet 192.168.2.0/24: DHCP mendistribusikan IP ke perangkat di subnet ini.
   
Alamat Gateway dan DNS server dikonfigurasi untuk setiap pool DHCP guna memastikan konektivitas jaringan yang lancar.

## Routing Dinamis dengan OSPF
Open Shortest Path First (OSPF) digunakan untuk mengaktifkan routing dinamis antar router.

Area 0 sebagai backbone yang menghubungkan seluruh subnet:
1. Subnet 172.16.1.0/24
2. Subnet 172.16.2.0/24
3. Subnet 192.168.1.0/24
4. Subnet 192.168.2.0/24
   
Keunggulan:
Routing otomatis tanpa perlu konfigurasi statis dan Perangkat dari subnet yang berbeda dapat saling berkomunikasi dengan mudah.
