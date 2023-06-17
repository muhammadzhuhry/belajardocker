# D.2. Volumes

Volume adalah direktori yang ada di luar container, tetapi dapat diakses oleh container. Volume ini bisa berada di dalam host atau di lokasi lain yang disediakan oleh driver volume Docker.

Beberapa kelebihan menggunakan volume:
- Data yang disimpan di volume tetap ada bahkan setelah container dihentikan atau dihapus.
- Volume dapat dibagikan dan digunakan oleh beberapa container secara bersamaan.
- Volume memudahkan developer dalam melakukan backup dan restore data container.

Berkut adalah cara menggunakan docker volume:
1. Membuat volume: <br/>
    Untuk membuat volume, gunakan command
    ```
    docker volume create
    ```
    Contoh: ```docker volume create myvolume```. Command ini akan membuat volume baru dengan nama "myvolume" yang nantinya dapat digunakan oleh container.
2. Menggunakan volume: <br/>
    Untuk menggunakan volume pada container, kita perlu mengaitkan volume dengan container saat menjalankanya. Gunakan opsi ```-v``` atau ```--volume``` saat menjalankan command ```docker run```, contoh: 
    ```
    docker run -v myvolume:/data myimage
    ```
    Pada command ini, volume "myvolume" akan di-mount ke dalam direktori "/data" di dalam container.
3. Melihat list volume: <br/>
    Kita dapat melihat list volume yang ada dengan menggunakan command: ```docker volume ls```. Command ini akan menampilkan list volume dan nama driver yang digunakan.
4. Menghapus volume:
    Untuk menghapus volume, gunakan perintah ```docker volume rm```, contoh:
    ```
    docker volume rm myvolume
    ```
    Pastikan bahwa volume tidak digunakan oleh container sebelum menghapusnya.
5. Penggunaan volumes di Docker Compose: <br/>
    Berikut adalah contoh konfigurasi penggunaan volume di Docker compose
    ```
    version: '3'
    services:
    myservice:
        ...
        volumes:
        - mydata:/app/data
    volumes:
    mydata:
    ```
    Dalam contoh di atas, volume dengan nama "mydata" didefinisikan di bagian akhir file docker-compose.yml dan kemudian digunakan dalam layanan myservice.