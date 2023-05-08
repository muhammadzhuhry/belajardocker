# A.1. Pengenalan Docker

Docker pertama kali dirilis pada tahun 2013 oleh Solomon Hykes dan timnya di Dotcloud, sebuah startup yang menawarkan platform as a service (PaaS). Awalnya Docker dibuat sebagai sebuah internal project di Dotcloud yang bertujuan untuk memudahkan pengembangan dan deployment aplikasi dalam lingkungan cloud. Namun, setelah melihat potensi besar Docker untuk membantu proses deployment dan portability aplikasi, Hykes dan timnya memutuskan untuk merilisnya sebagai project open source pada tahun yang sama. Sejak itu, Docker telah menjadi salah satu teknologi containerization paling populer dan banyak digunakan di seluruh dunia. Pada tahun 2019, Docker menjadi bagian dari Docker Inc., sebuah perusahaan teknologi yang berfokus pada developing dan providing containerization.

## A.1.1. Apa itu Docker?

Docker adalah sebuah platform open-source yang memungkinkan developer untuk membuat, mengelola, dan menjalankan aplikasi dalam enviroment terisolasi yang disebut container. Dengan menggunakan Docker, developer dapat membuat aplikasi beserta semua depedencynya ke dalam sebuah container, dan menjalankan container tersebut pada enviroment yang berbeda-beda.

## A.1.2. Kelebihan Docker

- Portability: Aplikasi yang berada di dalam container Docker dapat dijalankan di berbagai lingkungan seperti server, desktop, atau bahkan di cloud tanpa perlu melakukan perubahan pada aplikasi.
- Efficient: Docker memungkinkan penggunaan resource yang lebih efisien dan konsisten karena container hanya memerlukan resource yang dibutuhkan oleh aplikasi.
- Scalability: Docker memungkinkan aplikasi untuk di-scaling secara horizontal dan vertikal.
- Security: Dalam Docker, setiap container berjalan di enviroment yang terisolasi sehingga keamanan aplikasi terjaga.