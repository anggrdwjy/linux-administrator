## Dasar Terminal Linux
Terminal adalah aplikasi yang berbasis TUI (Text User Interface), pada setiap perintah yang akan dijalankan harus di masukkan melalui keyboard
| Perintah | Keterangan |
| --- | --- |
| ls -l | Menampilkan semua file dalam directory dengan format Panjang |
| mkdir "directory" | Membuat directory |
| rmdir "directory" | Menghapus directory dengan kriteria directory harus kosong |
| rmdir -r "directory" | Menghapus directory beserta isinya |
| cd /"directory" | Masuk kedalam suatu directory |
| cp "file/directory" | Mengcopy file/folder |
| cp -r "file/directory" | Mengcopy file/folder beserta file-nya |
| mv "file" "file"  | Melakukan rename file |
| mv "file" "directory/file"  | Memindahkan file ke folder |
| cat "file" | Menampilkan isi file |
| alias "script="command" | Memberi nama lain dari sebuah perintah. contoh; alias show="ls -l" |
| unalias "script="command" | Mengembalikan nama lain dari sebuah perintah dari "alias". contoh; unalias show |
| ps aux | Untuk melihat proses yang berjalan |
| kill "-id"| Mematikan proses yang berjalan dengan id proses |

Contoh mengetahui jumlah directory melalui "ls -l"
```
#Penanda
1 : file
2 : directory

#Jumlah directory
5 : Penanda 2 (Directory) + 3 (File)
```

## Managemen User & Group
Pengaturan user dan group di linux akan membuat lebih mudah dalam membagi setiap akun user dan tiap-tiap grup dalam mengatur hak kepemilikan file
| Perintah | Keterangan |
| --- | --- |
| useradd -m "user" | Menambahkan user |
| passwd "user" | Memberikan password pada user |
| groupadd "group" | Menambahkan group user baru |
| usermod -G "group" "user" | Memasukan user kedalam group |
| gpasswd -a "group" "user" | Memasukan user kedalam group |
| groupdel "group" | Menghapus group |
| chown "user.group" "file" | Menganti kepemilikan user (Owner) dan group |
| chgrp "group" "file" | Menganti kepemilikan group |
| userdel -r "user" | Menghapus user beserta folder dihome directory |
| pwd | Menampilkan directory aktif |
| su "user" | Pindah User |
| id "user" | Menampilkan ID User dan ID Group |
| whoami | Menampilkan user login pada saat digunakan |
| hostname | Menampilkan nama host pada saat digunakan |

| Directory | Keterangan |
| --- | --- |
| cat /etc/passwd | Mengetahui user di Linux |
| cat /etc/group | Mengetahui user tergabung dalam group |
| cat /etc/shadow | Mengetahui user dan password dalam bentuk "hash" |

Contoh membuat user menjadi administrator
```
nano /etc/sudoers

#Tambahkan
"user" ALL=(ALL:ALL) ALL
```

## CHOWN, CHGRP, dan CHMOD
CHOWN atau Change Ownership adalah perintah untuk mengganti user (owner) atau pemilik dari suatu file atau direktori. CHGRP atau Change Group adalah perintah untuk mengganti kepemilikan group pada suatu file atau direktori. CHMOD atau Change Mode adalah perintah untuk menambah dan mengurangi hak akses user dalam mengakses suatu file atau direktori
| Perintah | Keterangan | Contoh |
| --- | --- | --- |
| CHOWN | Change Ownership | Contoh; chown user.group file |
| CHGRP | Change Group | Contoh; chgrp group file |
| CHMOD | Change Mode | Contoh; chmod 777 file / chmod 777 directory |

Contoh melakukan CHMOD
```
chmod [ugoa] [=-+] [rwx] "file/directory"
chmod o+w /var/www/html
```

## Sistem Numeric Coding
Perijinan untuk user, group dan other yang didasarkan pada penggunaan kombinasi angka-angka. 
| Biner | Desimal | Hak |
| --- | --- | --- |
| 000 | 0 | Tidak memiliki hak apapun |
| 001 | 1 | Hak eksekusi |
| 010 | 2 | Hak menulis |
| 011 | 3 | Hak Menulis dan mengeksekusi |
| 100 | 4 | Hak membaca |
| 101 | 5 | Hak Membaca dan mengeksekusi |
| 110 | 6 | Hak Membaca dan menulis |
| 111 | 7 | Hak Membaca, menulis dan mengeksekusi |


## Sistem Letter Coding
Sistem ini dipakai untuk memberi hak akses kepada u (user), g (group), o (other) dan a (all), caranya dengan memberi tanda plus (+) untuk menambahkan hak akses dan tanda minus  (-) untuk menghapus
| Keterangan |
| --- |
| u adalah User (Owner) | 
| g adalah Group | 
| o adalah Other | 
| a adalah All | 
| = adalah Set sebagai satu-satunya hak akses yang dimiliki | 
| + adalah Penambahan izin - adalah non-aktifkan suatu izin | 
| r adalah Akses read (membaca) | 
| w adalah Akses write (Menulis) | 
| x adalah Akses execute (Mengekseksi) | 

## Find
Find adalah perintah yang umum digunakan untuk mencari file di sistem operasi linux.
| Perintah | Keterangan |
| --- | --- |
| find / -name apache2.conf | Mencari file apache.conf |
| find /home -name file | Mencari file/folder dengan membedakan huruf kapital  |
| find /home -iname File | | Mencari file/folder tanpa membedakan huruf kapital  |
| find /home -type d -name file | Mencari directory  |
| find /home -type f -name File | Mencari file  |
| fine /home -type f -perm 0777 -print | Mencari file dengan permission  |
| fine /home -type d -perm 0777 -print | Mencari directory dengan permission  |
| find /home -type f -perm 0777 -print -exec| chmod 644 {} ; /home/test/file | Mengganti permission pada file  |
| find /home -type d -perm 0777 -print -exec| chmod 644 {} ; /home/test/file | Mengganti permission pada directory  |
| find /home -type f -empty | Mencari file kosong  |
| find /home -type d -empty | Mencari directory kosong  |
| find /home -size 1M | Mencari folder dengan ukuran 1MB  |
| cat ~/.bash_history | Menampilkan history "bash" |

## Menggetahui Pengguna Lain di Server
| Perintah | Keterangan |
| --- | --- |
| who | Menampilkan pengguna yang sedang aktif |
| cat /var/log/auth.log | Menampilkan log pengguna yang login pada server |

## Reset Password User Linux Melalui Recovery Mode
Reset password Linux
1. Reboot Server
2. Advance options (from Bootloader)
3. Recovery Mode
4. Root (Drop to root shell prompt)
```
cat /etc/passwd | grep "user"
passwd "user"
```
5. resume

## Update Software Repository
Update Lokal Repository
```
nano /etc/apt/source.list
apt-get update
```

## Melihat IP Address dan Konfigurasi Netplan pada Linux
Cek IP Address
```
ip addr
ifconfig (Jika tidak bisa melakukan ifconfig, perlu menginstall "apt-get install net-tools"
```

Konfigurasi Netplan
```
nano /etc/netplan/50-cloud-init.yaml
```
```
## Static Konfigurasi
network:
	ethernets:
		ens0:
			addresses : "ip-add/netmask"
			gateway4 : "ip-add gateway"
			nameservers :
				addresses: "dns"
	version: 2

## Dynamic Konfigurasi
network:
	ethernets:
		ens0:
			dhcp4: true
	version: 2
```
```
netplan apply
```

## FTP dan SFTP pada Server Linux
Install FTP {Tidak direkomendasikan, kurang secure)
```
apt-get install proftpd
```
Menggunakan FTP
```
ftp://ip-addr
```

Sebelum Menggunakan SFTP, Edit konfigurasi sshd_config. Jika tidak ada sshd, Install OpenSSH lebih dahulu. 
```
nano /etc/ssh/sshd_config
```
Tambahkan di sshd_config
```
PermitRootLogin yes 
```
Restart SSH
```
service ssh restart
```
Tambahkan Password pada User
```
passwd "user"
```

## Domain Name Server
BIND (singkatan dari bahasa Inggris: Berkeley Internet Name Domain) adalah server DNS yang paling umum digunakan di Internet, khususnya pada sistem operasi bertipe Unix yang secara de facto merupakan standar

Install BIND
```
apt-get install bind9
```

backup db.local
```
cd /etc/bind
cp db.local db.domain.net
```
Edit db.local
```
nano db.domain.net

; BIND data file for local loopback interface 
; 
$TTL    604800 
@       IN      SOA     domain.net. root.domain.net. ( 
                              2         ; Serial 
                         604800         ; Refresh 
                          86400         ; Retry 
                        2419200         ; Expire 
                         604800 )       ; Negative Cache TTL 
; 
@       IN      NS      domain.net. 
@       IN      A       "ip-addr" 
@       IN      AAAA    ::1 
```

backup named.conf
```
cd /etc/bind
cp named.conf named.conf.bak
```

Edit named.conf
```
include "/etc/bind/named.conf.options"; 
include "/etc/bind/named.conf.local"; 
include "/etc/bind/named.conf.default-zones"; 
zone "domain.net" { 
  type master; 
  file "/etc/bind/db.domain.net"; 
  allow-transfer { 192.168.1.xx; }; 
}; 
```

Restart bind9
```
service bind9 restart
```

## SAMBA Server pada Linux
Samba adalah program yang bersifat open source yang menyediakan layanan berbagi berkas (file service) dan berbagi alat pencetak (print service), resolusi nama NetBIOS, dan pengumuman layanan (NetBIOS service announcement/browsing). 

Install Samba
```
apt-get install samba
```
Edit konfigurasi SAMBA
```
nano /etc/samba/smb.conf
```
```
[data]
	comment = Users profiles
	valid users = "username"
	path = /home/folder
	guest ok = yes
	browseable = yes
	writeable = yes
	create mask = 0600
	directory mask = 0700

[printers]
	comment = All Printers
	browseable = no
```
Memberi password pada folder dan akses
```
smbpasswd -a "username"
chmod o+w /home/folder
```
Restart SAMBA
```
service smbd restart
```

## Membangun Router pada Server Linux
Router berfungsi sebagai penghubung 2 jaringan atau lebih untuk meneruskan data dari satu jaringan ke jaringan lainnya. Server membutuhkan 2 port interface yang berbeda digunakan untuk UPLINK dan DOWNLINK.

Mendeteksi Interface pada Server
```
lshw -C network
```

Konfigurasi interface menggunakan netplan
```
nano /etc/netplan/50-cloud-init.yaml
```

Edit rc.local
```
nano /etc/rc.local

#!/bin/sh -e 
# 
# rc.local 
# 
# This script is executed at the end of each multiuser runlevel. 
# Make sure that the script will "exit 0" on success or any other 
# value on error. 
# 
# In order to enable or disable this script just change the execution 
# bits. 
# 
# By default this script does nothing. 
sudo sysctl -w net.ipv4.ip_forward=1 
/sbin/iptables -P FORWARD ACCEPT 
/sbin/iptables --table nat -A POSTROUTING -o "port" -j MASQUERADE 
```

Ubah Change Mode
```
chmod 777 rc.local
```

Aktifkan Router
```
systemctl enable rc-local 
```

## DHCP Server pada Server Linux
Protokol Konfigurasi Hos Dinamik (PKHD) (bahasa Inggris: Dynamic Host Configuration Protocol adalah protokol yang berbasis arsitektur client/server yang dipakai untuk memudahkan pengalokasian alamat IP dalam satu jaringan

Install DHCP Server
```
apt-get install isc-dhcp-server
```

Backup dhcp.conf
```
cd /etc/dhcp
mv dhcpd.conf dhcpd.conf.bak
```

Edit dhcp.conf
```
default-lease-time 600; 
max-lease-time 7200; 
option subnet-mask 255.255.255.0; 
option broadcast-address 192.168.10.255; 
option routers 192.168.10.1; 
option domain-name-servers 8.8.8.8, 8.8.4.4; 
option domain-name "mydomain.example"; 
subnet 192.168.10.0 netmask 255.255.255.0 { 
range 192.168.10.10 192.168.10.100; 
range 192.168.10.150 192.168.10.200; 
}
```

Perintah merestart, menjalankan dan mematikan DHCP Server
```
sudo service isc-dhcp-server restart 
sudo service isc-dhcp-server start 
sudo service isc-dhcp-server stop 
```

## VPN PPTP Server pada Linux
A PPTP tunnel is instantiated by communication to the peer on TCP port 1723. This TCP connection is then used to initiate and manage a GRE tunnel to the same peer.

Install VPN PPTP
```
apt-get install pptpd
```

Konfigurasi pptp.conf
```
nano /etc/pptpd.conf

localip 192.168.10.1 
remoteip 192.168.10.100-200,192.168.10.201 
```

Konfigurasi Secret
```
nano /etc/ppp/chap-secrets

#client server secret IP address
user1 pptpd "password" *
```

Konfigurasi DNS
```
nano /etc/ppp/pptpd-options

ms-dns 8.8.8.8
ms-dns 8.8.4.4
```

Restart VPN
```
service pptpd restart
```

## Port Forwarding pada Server Linux
Port forwarding allows remote computers (for example, computers on the Internet) to connect to a specific computer or service within a private local-area network (LAN)

Tambahkan IPTABLES
```
sudo sysctl -w net.ipv4.ip_forward=1 
iptables -t nat -A PREROUTING -j DNAT -d 192.168.1.20 -p tcp --dport 80 --to 192.168.10.2
```
