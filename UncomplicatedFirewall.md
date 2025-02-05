## Firewall di Linux
Scanning Firewall menggunakan NMAP
```
nmap ip-addr
nmap -A ip-addr
nmap -sn ip-addr/mask
```

## Dasar Perintah Firewall
| Perintah | Keterangan |
| --- | --- |
| ufw enable | Mengaktifkan Firewall |
| ufw allow 23 | Membuka port 23 (Telnet) |
| ufw allow 22 | Membuka port 22 (SSH) |
| ufw allow 80 | Membuka port 80 (HTTP) |
| ufw allow 443 | Membuka port 443 (HTTPS) |
| ufw deny 80 | Tenggang waktu tersambung habis (HTTP) |
| ufw reject 80 | Tidak dapat tersambung (closed) |
| ufw status | Menampilkan status aktif port pada firewall |
| ufw reset | Reset firewall |
| ufw delete 1 | Menghapus rule pada baris 1 |
| ufw delete 2 | Menghapus rule pada baris 2 |

## Cara Blokir IP
| Perintah | Keterangan |
| --- | --- |
| ufw insert 1 deny from ip-addr to any | Memblokir IP address tertentu |
| ufw delete 1 deny from ip-addr to any | Menghapus IP address tertentu yang di blokir |
| ufw allow from ip-addr to any port 22 | Memblokir semua IP address kecuali IP address tertentu diport 22 |
| ufw allow from ip-addr to any port 80 | Memblokir semua IP address kecuali IP address tertentu diport 80 |

Contoh Blokir IP menggunakan Ubuntu 2x.xx
```
sudo ufw deny from ip-addr
ufw allow 80
```
