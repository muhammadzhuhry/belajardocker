# B.2. Docker Container

Docker container merupakan instance dari docker image yang dapat dijalankan secara terisolasi dari host machine.

Dalam Docker, sebuah container dapat dibuat dan dijalankan menggunakan Docker CLI atau melalui Docker API. Ketika sebuah container dijalankan, Docker mengalokasikan sumber daya seperti CPU, RAM, dan storage secara terpisah dari sumber daya host dan container lainnya.

Dalam pembuatan sebuah Docker Container, terdapat beberapa faktor yang perlu diperhatikan, antara lain penggunaan base image yang tepat, konfigurasi environment, pengaturan resource allocation, dan lain sebagainya. Selain itu, penggunaan Dockerfile dan Docker Compose juga dapat mempermudah proses pembuatan dan pengelolaan container.

## B.2.1. Docker Container Command
Beberapa command yang sering digunakan di Docker container antara lain:
1. Melihat daftar container:
    ``` 
    docker container ls
    ```
    ``` 
    docker container ls -a
    ```
    kedua command diatas digunakan untuk melihat list container, perbedaanya di command yang terdapat flag -a akan menampilkan semua container baik yang sedang run maupun stop.
2. Membuat container:
    ```
    docker container create <nama_image:tag>
    ```
    Contoh penggunaan command untuk membuat container dengan docker container create adalah sebagai berikut:
    ```
    docker container create --name nginx_container nginx:latest
    ```
3. Menjalankan container:
    ```
    docker container start <nama_container>
    ```
    Contoh penggunaan command docker container start:
    ```
    docker container start nginx_container
    ```
    Selaing menggunakan command docker container start, kita bisa juga menggunakan command:
    ```
    docker run <nama_image>
    ```
    Ketika menggunakan docker run, secara otomatis container baru akan dibuat dan langsung dijalankan.
4. Menghentikan container:
    ```
    docker container stop <nama_container>
    ```
5. Menghapus container:
    ```
    docker container rm <nama_container>
    ```

## B.2.2. Options yang biasa digunakan
Berikut adalah beberapa option yang sering digunakan:
- -i atau --interactive: Menjalankan container dalam mode interaktif
- -t atau --tty: Mengalokasikan terminal pseudo-TTY
 - --name: Memberikan nama pada container yang dibuat
 - -p atau --publish: Meneruskan port dari host ke container
 - -v atau --volume: Menyematkan volume dari host ke container
 - --network: Menghubungkan container ke network
 - -e atau --env: Menetapkan enviroment variabel pada container yang dibuat

Berikut merupakan contoh lengkap penggunaan option ketika membuat container baru:
```
docker container create --name mysql_container -e MYSQL_ROOT_PASSWORD=password -p 3306:3306 mysql:latest
```
Disini kita membuat container baru dengan nama mysql_container, lalu mengatur env variable MYSQL_ROOT_PASSWORD=password, mengexpost port 3306 di host dan container serta menggunakan image mysql latest.