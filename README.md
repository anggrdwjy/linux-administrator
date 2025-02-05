## Dasar Terminal Linux
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


## Managemen User & Group
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
| who | Menampilkan pengguna yang sedang aktif |
| whoami | Menampilkan user login pada saat digunakan |
| hostname | Menampilkan nama host pada saat digunakan |


## Sistem Numeric Coding
| Perintah | Keterangan | Contoh |
| --- | --- | --- |
| CHOWN | Change Ownership | Contoh; chown user.group file |
| CHGRP | Change Group | Contoh; chgrp group file |
| CHMOD | Change Mode | Contoh; chmod 777 file / chmod 777 directory |

Example
```
chmod [ugoa] [=-+] [rwx] "file/directory"
```
