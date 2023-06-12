# C.2. Penggunaan Bridge Network Driver

Berikut adalah contoh pengimplementasian Bridge network dengan study case membuat container service Node.js yang terkoneksi ke mongodb.

1. Buat network baru dengan driver bridge:
    ``` 
    docker network create mynetwork
    ```
2. Jalankan container MongoDB dan hubungkan ke network yang sebelumnya dibuat:
    ```
    docker run -d --name mongocontainer --network mynetwork mongo
    ```
    Pada command diatas, kita menjalankan container MongoDB dengan nama "mongocontainer" menggunakan image mongo, dan menghubungkanya ke network "mynetwork".

3. Buat service Node.js dengan file `app.js` yang berisikan kode berikut:
    ```
    const express = require('express');
    const app = express();
    const port = 3000;

    // Membuat koneksi ke MongoDB
    const MongoClient = require('mongodb').MongoClient;
    const url = 'mongodb://mongocontainer:27017/mydatabase';

    app.get('/', (req, res) => {
      // Melakukan operasi database MongoDB
      MongoClient.connect(url, function(err, client) {
        if (err) {
          res.send(Failed connect to MongoDB');
        } else {
          res.send('Succes connect to MongoDB');
          client.close();
        }
      });
    });

    app.listen(port, () => {
      console.log(`Service running on port ${port}`);
    });
    ```
4. Buat Dockerfile yang berisikan command berikut:
    ```
    FROM node:latest
    WORKDIR /app
    COPY package.json .
    RUN npm install
    COPY . .
    EXPOSE 3000
    CMD [ "node", "app.js" ]
    ```
    Dockerfile diatas akan membuat image yang menjalankan service Node.js dengan file `app.js` yang telah dibuat sebelumnya.
5. Build image dari Dockerfile:
    ```
    docker build -t nodeapp .
    ```
    Perintah di atas akan membuat image dengan nama nodeapp berdasarkan Dockerfile yang telah dibuat.
6. Jalankan container service Node.js dengan menghubungkanya ke network yang telah dibuat:
    ```
    docker run -d --name nodecontainer --network mynetwork -p 3000:3000 nodeapp
    ```
    Dalam contoh ini, kita menjalankan container service Node.js dengan nama "nodecontainer" menggunakan image nodeapp yang telah kita build sebelumnya. Container tersebut juga dihubungkan ke network "mynetwork" dan melakukan port forwarding dari port 3000 pada host ke port 3000 pada container.

Setelah container running, "nodecontainer" akan dapat terhubung ke database MongoDB yang berjalan pada container "mongocontainer" dalam network yang sama. Anda dapat mengakses service "nodecontainer" ini melalui http://localhost:3000 pada browser Anda.

Ini adalah contoh sederhana pengimplementasian network dengan driver Bridge dalam Docker untuk menghubungkan container service Node.js dengan database MongoDB. Dengan menggunakan network ini, aplikasi dan database dapat berkomunikasi satu sama lain dalam network yang sama.