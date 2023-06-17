# D.1. Docker Storage

Docker storage adalah istilah yang mengacu pada cara Docker mengelola dan menangani penyimpanan data yang berhubungan dengan container. Docker menyediakan beberapa opsi untuk mengelola dan menyimpan data container.

Dalam Docker, terdapat beberapa komponen storage yang perlu dipahami:

1. **Container Storage**: Merujuk pada data yang ada di dalam container itu sendiri. Ketika sebuah container berjalan, semua perubahan yang terjadi pada file sistem dalam container disimpan di layer overlay yang dikenal sebagai "container layer". Setiap container memiliki container layer yang unik.
2. **Image Storage**: Merupakan penyimpanan untuk Docker images. Setiap image terdiri dari satu atau beberapa layer yang tersusun secara hierarkis. Setiap layer berisi perubahan file sistem terhadap layer sebelumnya. Image storage mencakup image cache, yang digunakan untuk mengoptimalkan proses build dan deployment container.
3. **Volume Storage**: Digunakan untuk menyimpan data persisten yang terkait dengan container. Volume memungkinkan data di dalam container tetap ada dan dapat diakses bahkan setelah container di stop atau di delete. Volume storage terpisah dari container layer, sehingga data yang disimpan dalam volume tidak akan hilang saat container dihapus.
4. **Bind Mounts**: Merupakan cara untuk menghubungkan direktori atau file dari host sistem operasi ke dalam container. Dengan bind mounts, kita dapat menyimpan dan mengakses data dari luar container. Perubahan yang terjadi pada bind mounts juga akan terlihat di host dan sebaliknya.