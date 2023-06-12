# B.4. Dockerfile

Dockerfile adalah sebuah file yang berisi intruksi untuk membangun sebuah Docker image. Dockerfile memungkinkan kita untuk mendefiniskan dengan jelas langkah-langkah yang diperlukan untuk membuat image yang sesuai dengan kebutuhan aplikasi kita.

## B.4.1. Membuat Dockerfile
Berikut adalah step dan penjelasan lebih rinci terkait pembuatan Dockerfile:
1. Base image:
  - Dockerfile dimulai dengan menentukan base image yang akan digunakan sebagai dasar untuk membangun image baru. Base image ini bisa berupa image resmi yang disediakan oleh Docker Hub atau image custom yang sudah dibuat sebelumnya.
  - Contoh: ```FROM node:14```
2. Set working directory:
  - Anda bisa menentukan working directory di dalam container.
  - Contoh: ```WORKDIR /app```
3. Copy files:
  - Dalam Dockerfile, Anda dapat menyalin file dan direktori dari host ke dalam image yang sedang dibangun. Ini memungkinkan Anda untuk menyertakan config file, source code, atau file lain yang diperlukan oleh aplikasi di dalam image.
  - Contoh: ```COPY package*.json ./```
4. Run command:
  - Anda dapat menjalankan perintah-perintah shell di dalam Dockerfile. Ini bisa berupa command untuk install dependensi, atau melakukan tugas-tugas lain yang dibutuhkan untuk mengatur image dengan benar.
  - Contoh: ```RUN npm install```
4. Set ENV:
  - Dockerfile memungkinkan Anda untuk menetapkan ENV yang diperlukan oleh aplikasi saat berjalan di dalam container. Ini dapat mencakup pengaturan config, credential, dsb.
  - Contoh: ```ENV DB_HOST=localhost```
5. Expose Port:
  - Anda dapat menentukan port yang akan diekspos oleh container. Ini memungkinkan traffic masuk ke container melalui port tersebut.
  - Contoh: ```EXPOSE 8080```
6. Set Default command:
  - Anda dapat menentukan command default yang akan dieksekusi saat container berjalan. Ini biasanya merupakan command yang menginisialisasi dan menjalankan aplikasi utama.
  - Contoh: ```CMD [ "npm", "start" ]```

Berikut contoh Dockerfile untuk Aplikasi Node.js:

```
# Menggunakan Node.js sebagai base image
FROM node:14

# Menentukan direktori kerja di dalam container
WORKDIR /app

# Menyalin file package.json dan package-lock.json ke dalam direktori kerja
COPY package*.json ./

# Menjalankan perintah npm install untuk menginstal dependensi aplikasi
RUN npm install

# Menyalin seluruh konten project ke dalam work dir
COPY . .

# Menentukan ENV
ENV DB_HOST=localhost:3306

# Menentukan port yang akan diekspos oleh container
EXPOSE 8080

# Menjalankan perintah default untuk menjalankan aplikasi Node.js
CMD [ "npm", "start" ]

```

## B.4.2. Build image dari Dockerfile

Berikut adalah langkah-langkah yang umum dilakukan dalam membuild image dari Dockerfile:

1. Untuk melakukan build gunakan command:
 ```docker build``` diikuti juga dengan argument yang sekiranya dibutuhkan:
    ```
    docker build -t image_name:tag -f Dockerfile .
    ```
    - -t image_name:tag digunakan untuk memberikan nama dan tag pada image yang akan dibuild. Nama image biasanya disesuaikan dengan aplikasi atau service yang ingin Anda jalankan di dalam container.
    - -f Dockerfile digunakan untuk menentukan path atau nama Dockerfile jika tidak berada di direktori saat ini.
    - . menunjukkan bahwa build akan dilakukan pada direktori saat ini, di mana Dockerfile berada.
2. Untuk menjalankan container dari image yang barusan di build gunakan perintah: ```docker run``` contohnya:
    ```
    docker run -d -p 8080:80 image_name:1.0
    ```