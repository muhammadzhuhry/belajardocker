# C.1. Docker Network

## C.1.1. Pengenalan Docker Network

Di dalam enviroment Docker, setiap container memiliki IP address yang terisolasi satu sama lain. Kita bisa menggunakan fitur Docker Network agar suatu container bisa berkomunikasi dan berinteraksi dengan container yang lain. 

## C.2.1. Network Driver

Berikut adalah jenis-jenis driver yang sering digunakan di Docker Network:

- Bridge </br>
Bridge network merupakan driver default yang digunakan Docker. Ketika kita menjalankan suatu container tanpa menentukan driver network yang digunakan, maka secara otomatis Docker akan menggunakan driver Bridge ini. Lalu, setiap container yang berada di dalam Bridge network ini akan dapat saling berkomunikasi.

- Host </br>
Di dalam Host network, container tidak diisolasi dari host dan dapat mengakses host network resources secara langsung. Namun, ini juga berarti port yang digunakan oleh container tidak dapat digunakan oleh container lain atau aplikasi di host.

- Overlay </br>
Overlay network digunakan untuk menghubungkan container yang berjalan di mesin yang berbeda serta network yang juga berbeda. Ini memungkinkan komunikasi antar container yang terdistribusi di berbagai mesin fisik.