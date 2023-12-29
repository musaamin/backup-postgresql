# PostgreSQL Backup Tool

Program sederhana untuk melakukan backup PostgreSQL database dan sinkronisasi direktori backup ke cloud storage. Program ini memanfaatkan `psql_dump` untuk export database dan `rclone` untuk sinkronisasi ke cloud.

## Cara Install
Download `backup-postgresql`

```
sudo wget https://raw.githubusercontent.com/musaamin/backup-postgresql/main/backup-postgresql -O /usr/local/bin/backup-postgresql
sudo chmod +x /usr/local/bin/backup-postgresql
```

## Cara Menggunakan
Membuat file konfigurasi yang berisi informasi database dan backup.

```
backup-postgresql init mydb.txt
```

Atur file konfigurasi `mydb.txt`.
User yang digunakan memiliki akses Superuser.

```
DBHOST=localhost
DBPORT=5432
DBNAME=mydatabase
DBUSER=myuser
DBPASS=mypassword
BACKUPDIR=/path/to/backup
RCLONEREMOTES=remote1, remote2
RCLONEDIR=cloud-dir/backup
```

Melakukan backup database.

```
backup-postgresql export mydb.txt
```

Melakukan sinkronisasi direktori backup ke cloud storage.

```
backup-postgresql rclone mydb.txt
```