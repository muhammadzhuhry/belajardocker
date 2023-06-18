# E.1. Study Case Aplikasi Node.js

Berikut adalah study case sederhana, membuat aplikasi yang mengembalikan server time yang dibuat menggunakan Node.js, selain itu kita juga akan menggunakan Dockerfile dan juga docker-compose.

1. Getting started:
    - Pastikan Node.js sudah terinstall
    - Buat direktori baru untuk project yang akan dibuat ini
2. Initiate Project & Install Dependencies:
    - Jalankan command ```npm init -y``` di dalam direktori project untuk melakukan inisialisasi project Node.js baru.
    - Install Express.js sebagai depedency dengan menggunakan command: ```npm install express```
3. Buat file server.js:
    - Buat file server.js dalam direktori project dan buka file tersebut
    - Tulis kode berikut di dalam file server.js:
      ```
      const express = require('express');

      const app = express();
      const port = 8000;

      app.get('/', (req, res) => {
        res.send(`Server Time: ${new Date().toISOString()}`);
      });

      app.listen(port, () => {
        console.log(`Server running on port ${port}`);
      });
      ```
      Kode di atas menggunakan Express untuk membuat server HTTP sederhana yang akan mengembalikan server time setiap kali permintaan GET diterima.
4. Buat Dockerfile:
    - Buat file Dockerfile dalam direktori project dan buka file tersebut
    - Tulis kode berikut di dalam Dockerfile:
      ```
      # Menggunakan Node.js versi terbaru sebagai base image
      FROM node:latest

      # Set working directory di dalam container
      WORKDIR /app

      # Menyalin package.json dan package-lock.json untuk menginstal dependencies
      COPY package*.json ./

      # Menginstal dependencies
      RUN npm install

      # Menyalin kode project ke dalam container
      COPY . .

      # Expose port yang digunakan oleh aplikasi
      EXPOSE 8000

      # Menjalankan aplikasi saat container di-start
      CMD [ "node", "server.js" ]
      ```
      Dockerfile di atas mendefinisikan langkah-langkah untuk membangun image Docker dari project Node.js Anda. Dependensi diinstal, kode project disalin ke dalam container, dan aplikasi dijalankan saat container di-start.
5. Buat Docker Compose File:
      - Buat file docker-compose.yml dalam direktori project dan buka file tersebut
      - Tulis kode berikut di dalam docker-compose.yml:
        ```
        version: '3'
        services:
          app:
            build:
              context: .
              dockerfile: Dockerfile
            ports:
              - 8000:8000
        ```
        Docker Compose file di atas mendefinisikan service app. Service app menggunakan Dockerfile yang telah dibuat sebelumnya untuk membuild image dan melakukan expose port ke port 8000 pada host. Layanan redis menggunakan citra Redis yang tersedia di Docker Hub.
6. Jalankan Aplikasi:
    - Buka terminal atau command prompt dan pastikan Anda berada di direktori project.
    - Jalankan command docker-compose up untuk menjalankan aplikasi. Docker Compose akan membuild image dan menjalankan container untuk aplikasi Node.js ini.
    - Akses http://localhost:8000 di browser Anda, dan Anda akan langsung melihat server time.