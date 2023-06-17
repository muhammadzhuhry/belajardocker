# D.3. Bind Mounts

 Bind mounts memungkinkan Developer untuk melakukan bind direktori atau file dari host ke dalam container. Ini berarti data di dalam direktori tersebut akan tersedia di kedua sisi, baik di host maupun di container. Perubahan yang dilakukan pada data di salah satu sisi akan terlihat secara real-time di sisi lainnya.Perbedaan utama antara bind mounts dengan volumes adalah bahwa bind mounts menggunakan direktori yang ada di host sebagai sumber datanya, sedangkan volumes menggunakan direktori yang dikelola oleh Docker.

 Beberapa kelebihan menggunakan bind mount:
 - Data di bind mounts akan tetap ada dan tidak hilang ketika container dihentikan atau dihapus.
 - Developer dapat mengubah atau menghapus data di bind mounts tanpa mempengaruhi image atau container.

 Berkut adalah cara menggunakan bind mounts:
 1. Tentukan path file atau direktori pada host yang ingin kita bind mount ke dalam container.
 2. Saat menjalankan container, tambahkan opsi ```-v``` atau ```--volume``` pada command docker run untuk menentukan bind mount. Format umumnya adalah:
    ``` 
    docker run -v /path/on/host:/path/in/container ...  
    ```
    Di sini, "/path/on/host" adalah direktori pada host yang ingin kita bind mount, sedangkan "/path/in/container" adalah path di dalam kontainer tempat bind mount akan dilakukan. <br/>
    Contoh penggunaan bind mount untuk melakukan bind direktori mydata pada host ke dalam direktori /app/data di container:
    ```
    docker run -v /absolute/path/to/mydata:/app/data ...
    ```
    Penting untuk diketahui bahwa path pada host harus merupakan path absolut (absolute path).
3. Lanjutkan dengan menjalankan command atau container sesuai kebutuhan. Sekarang, direktori atau file pada host yang kita bind mount akan tersedia di dalam container di path yang ditentukan.
4. Jika ingin menggunakan bind mount dengan Docker Compose, Kita dapat menambahkan konfigurasi bind mount ke dalam file docker-compose.yml. Berikut adalah contohnya:
      ```
      version: '3'
      services:
        myservice:
          ...
          volumes:
            - /absolute/path/to/mydata:/app/data
      ```