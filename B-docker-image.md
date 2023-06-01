# B.1. Docker Image

Docker image merupakan template yang berisi konfigurasi serta depedency yang diperlukan untuk menjalankan sebuah aplikasi. Image ini berfungsi sebagai blueprint untuk membuat sebuah container.

Docker image terdiri dari beberapa layer. Setiap layer merepresentasikan perubahan pada image, seperti tambahan package, perubahan konfigurasi, atau penambahan file.

Setiap layer pada image ini bersifat read-only, sehingga ketika ada perubahan pada image, Docker akan menambahkan layer baru dan membangun image yang baru berdasarkan layer-layer yang telah ada.

![Container Layers](img/B_container_layers.jpeg)

Layer paling bawah adalah base image, yang merupakan fondasi dari image tersebut. Setiap layer di atasnya merepresentasikan perubahan yang diterapkan ke base image. Layer-layer ini disusun secara bertumpuk, membentuk sebuah image yang lengkap.

Dengan menggunakan konsep layer ini, Docker dapat melakukan caching, sehingga ketika sebuah image telah di build lalu di modify, Docker hanya akan rebuild layer yang berubah saja, dan tidak perlu build ulang layer yang sama seperti sebelumnya. Hal ini membuat proses development dan deployment menjadi lebih cepat dan efisien.

## B.1.1. Docker Image Command
Beberapa command yang sering digunakan di Docker image antara lain:

1. Melihat images yang ada di local machine:
    ``` 
    docker image ls
    ```
2. Download(pull) image dari Docker Hub:
    ```
    docker pull image <nama_image>
    ```
3. Melihat detail image:
    ```
    docker image inspect <nama_image / ID_image>
    ```
3. Menghapus image:
    ```
    docker image rm <nama_image / ID_image>
    ```