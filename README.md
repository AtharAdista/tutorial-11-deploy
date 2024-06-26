### Nama : Shaquille Athar Adista
### Kelas : C

1. Membuka logs pertama kali sebelum menjalankan services
![alt text](img/logs1.png)

   Membuka logs setelah menjalankan servcies untuk pertama kalinya
![alt text](img/logs2.png)
   Membuka logs setelah menjalankan servcies untuk kedua kalinya
![alt text](img/logs3.png)

     Pada gambar terlihat perbedaan di bagian `GET /`, Awalnya kita tidak mencatat request apapun pada logs, namun setelah service di expose maka pada log akan tercatat `GET /`, hal ini terjadi karena setelah service di expose maka service dapat menerima request dan setiap request yang diterima akan dicatat ke dalam logs.
    
2. Perbedaan antara penggunaan `-n` dan tanpa `-n` pada `kubectl get` adalah  `-n` digunakan jika kita ingin menspesifik namespace yang ditargetkan, hal ini akan sangat berguna jika kita memiliki beberapa namespace di dalam kluster kubernetes kita. Jika kita menggunakan `kubectl get` tanpa `-n` maka kubectl akan menggunakan namespace default. Alasan mengapa pods/service yang sudah saya buat tidak muncul di output ketika menggunakan `kubectl get pods,services -n kube-system` adalah dikarenakan kubectl sudah menspesifikan namespace `kube-sytem` sehingga hanya data yang ada pada namaspace `kube-system` saja yang muncul.

### Rolling Update & Kubernetes Manifest File

1. Perbedaan antara rolling update dengan recreate deployment adalah dalam rolling update, instance baru dari pod dijalankan satu persatu sambil secara bertahap menghentikan dan menggantikan instance lama dengan yang baru. Hal ini membuat aplikasi akan tetap berjalan tanpa downtime yang signigikan. Sedangkan dalam recreate deployment. semua instancte pod dihentikan secara bersamaan dan kemudian diperbarui dengan instance baru yang memuat versi terbaru dari aplikasi. Hal ini akan menyebabkan aplikasi akan mengalami downtime selama proses pembaruan.

2. set up 
   ![alt text](img/set-up.png)

   edit deployment

   ![alt text](img/edit.png)

   ganti ke versi terbaru

   ![alt text](img/edited.png)

   delete pod

   ![alt text](img/delete_pods.png)

   akan dibuat ulang pod menggatikan pod yang sudah dihapus

   ![alt text](img/get-pods.png)

   run dan akan open swagger
   
   ![alt text](img/run.png)
   ![alt text](img/swagger.png)


3. Strategi dengan menggunakan rollingUdate

   ![alt text](img/strategy-1.png)

   Strategi dengan menggunakan Recreate

   ![alt text](img/strategy-2.png)

   Jalankan yaml yang sudah kita buat dan akan terlihat bahwa strategy yang diterapkan adalah recreate.Penjelasan gambar adalah kita set image baru agar pod lama di repliclas lama terhapus dan akan dibuat pod baru di repliclas baru dapat terlihat saat menjalankan get replicates.
   ![alt text](img/set-up-yaml.png)

   ![alt text](img/get-pods.png)

   ![alt text](img/get-replicates.png)

   Disini untuk mengganti strategi yang ingin digunakan kita dapat mengganti `strategy` dan `type` sesuai dengan kebutuhan.

4. Keuntungan dari memakai manifest file di kubernetes adalah efisiensi dikarenakan kita tidak perlu melakukan proses secara manual dan bisa langsung automasi sesuai file yang kita terapkan. Selain itu dengan menggunakan manifest file kita dapat memastikan konfigurasi aplikasi dan infrastrukur kubernetes yang kita produksi dan kelola sudah pasti konsisten di berbagai lingkungan. Manifest file juga dapat disimpan sehingga memungkinkan untuk melacak perubahan yang terjadi dan melakukan rollback serta berkolaborasi dengan anggota tim dalam pengembangan dan pengelolaan aplikasi.
