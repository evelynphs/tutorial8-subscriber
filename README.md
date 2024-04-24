a. What is AMQP? <br>
   AMQP adalah singkatan dari _Advaced Messaging Queuing Protocol_ yang merupakan salah satu standar _messaging protocol_. Standar ini digunakan untuk komunikasi antara dua sistem yang dilakukan dengan pengiriman dan penerimaan data.

b. what it means? guest:guest@localhost:5672, what is the first quest, and what is the second guest, and what is localhost:5672 is for? <br>
   `guest:guest@localhost:5672` merupakan sebuah URI yang digunakan untuk messaging dan networking dalam suatu sistem. Bagian `guest:guest`, merepresentasikan username dan password yang digunakan untuk autentikasi. `guest` di sebelah kiri tanda `:` merupakan username, dan `guest` di sebelah kanan merupakan password. Bagian `localhost:5672` merepresentasikan IP dan port yang digunakan untuk membuat koneksi. `localhost` merupakan IP yang me-refer ke mesin yang mengirimkan request itu sendiri, sedangkan `5672` merupakan nomor port yang digunakan.

<br>

### Simulation slow subscriber
![Simulation slow subscriber](/assets/images/running-rabbit-mq3.png)
Pada grafik queued messages, terlihat bahwa jumlah queue mencapai 10 dan grafik terlihat tajam. Artinya, sepuluh message memasukki message broker dalam waktu yang singkat dan menunggu untuk diproses. Pada grafik messages rate, garis ungu yang merepresentasikan consumer terlihat landai dan berada pada rentang waktu yang cukup panjang. Hal ini menandakan bahwa consumer pada subscriber membutuhkan waktu yang cukup lama untuk memproses message yang mengantre. Kecepatan subscriber dalam memproses message lebih lama dibandingkan kecepatan publisher dalam mengirim message.

<br>

### Running at least three subscribers
![Reflection and Running at least three subscribers](/assets/images/console3.png)
![Reflection and Running at least three subscribers 2](/assets/images/running-rabbit-mq4.png)
Kali ini, subscriber dijalankan pada tiga console yang berbeda sehingga proses terhadap message yang masuk terdistribusi pada ketiga console tersebut. Dapat dilihat bahwa grafik queued messages tetap datar, menandakan bahwa tidak ada queue/antrean message karena semua message telah diproses dengan cepat oleh ketiga console tersebut. Tidak ada message yang perlu menunggu untuk diproses karena proses kali ini berjalan lebih cepat. Proses kali ini berjalan lebih cepat karena proses terhadap message terdistribusi pada lebih dari satu subscriber sehingga beban tugasnya "terbagi tiga" dan beban tugas untuk setiap console menjadi lebih ringan dibandingkan apabila semua bebannya hanya ditumpuk pada satu console.




