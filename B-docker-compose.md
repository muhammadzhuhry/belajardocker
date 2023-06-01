# B.5. Docker Compose

## B.5.1. Pengenalan Docker Compose
Docker Compose adalah tool yang digunakan untuk mendefinisikan serta menjalankan satu atau lebih container.Pada implementasinya, developer dapat mendefenisikan command dan konfigurasi di dalam sebuah file YAML yang biasa disebut "docker-compose.yml".

File docker-compose.yml memungkinkan kita untuk mengonfigurasi beberapa komponen aplikasi, seperti containers, networks, volumes, enviroment variables, dan lain-lain. Anda dapat start, stop, dan manage aplikasi yang terdiri dari beberapa container dengan simple command menggunakan Docker Compose. Selain itu, dengan menggunakan file konfigurasi docker-compose.yml, developer lain dapat dengan mudah replicate enviroment yang sama, yang membuat proses development dan testing menjadi lebih konsisten dan manageable.

## B.5.2. Contoh penggunaan Docker Compose
Berikut adalah contoh penggunaan Docker Compose sederhana:
Membuat server backend dengan Nodejs yang terkoneksi ke database server mysql.
```
version: '3'
services:
  backend:
    image: node:14
    ports:
      - 3000:3000
    volumes:
      - ./backend:/app
    environment:
      - NODE_ENV=production
    command: npm start
  database:
    image: mysql:8
    environment:
      - MYSQL_ROOT_PASSWORD=password
      - MYSQL_DATABASE=mydb
```
Pada contoh ini, kita mendefinisikan dua service: backend dan database. 
- Service backend menggunakan image node:14 
- Mengekspos port 3000 dari container ke host 
- Mounts volume host ./backend ke direktori /app di container
- Set enviroment variable NODE_ENV ke "production"
- dan menjalankan command npm start saat container starts
- Service database menggunakan image mysql:8
- Set enviroment variable  MYSQL_ROOT_PASSWORD dan MYSQL_DATABASE.

Dengan menjalankan command ```docker-compose up``` di direktori yang berisi file Docker Compose ini, Docker Compose akan membaca file konfigurasi, build dan run container sesuai dengan definisi yang ada.