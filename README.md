### Nama : Shaquille Athar Adista
### Kelas : C

1. Membuka logs pertama kali sebelum menjalankan services
![alt text](img/logs1.png)

   Membuka logs setelah menjalankan servcies untuk pertama kalinya
![alt text](img/logs2.png)
   Membuka logs setelah menjalankan servcies untuk kedua kalinya
![alt text](img/logs3.png)

     Pada gambar terlihat perbedaan di bagian `GET /`, Awalnya kita tidak mencatat request apapun pada logs, namun setelah service di expose maka pada log akan tercatat `GET /`, hal ini terjadi karena setelah service di expose maka service dapat menerima request dan setiap request yang diterima akan dicatat ke dalam logs.
    
1. Perbedaan antara penggunaan `-n` dan tanpa `-n` pada `kubectl get` adalah  `-n` digunakan jika kita ingin menspesifik namespace yang ditargetkan, hal ini akan sangat berguna jika kita memiliki beberapa namespace di dalam kluster kubernetes kita. Jika kita menggunakan `kubectl get` tanpa `-n` maka kubectl akan menggunakan namespace default. Alasan mengapa pods/service yang sudah saya buat tidak muncul di output ketika menggunakan `kubectl get pods,services -n kube-system` adalah dikarenakan kubectl sudah menspesifikan namespace `kube-sytem` sehingga hanya data yang ada pada namaspace `kube-system` saja yang muncul.