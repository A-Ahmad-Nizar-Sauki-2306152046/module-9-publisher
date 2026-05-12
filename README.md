## a. Berapa banyak data yang dikirim program publisher ke message broker dalam satu kali run?

Pada pertama kali program `publisher` dijalankan, program akan mengirim **5 pesan** ke message broker. Hal ini karena di dalam kode terdapat beberapa pemanggilan `publish_event()` yang masing-masing mengirim satu event.

Setiap event berisi data `UserCreatedEventMessage`, yang memiliki dua field:

- `user_id` (String)
- `user_name` (String)

Jika melihat isi data, setiap pesan berukuran kecil karena hanya mengirim teks berupa ID dan nama user. Jadi total data yang dikirim dalam satu kali run adalah gabungan dari 5 pesan tersebut, yaitu sejumlah isi string dari masing-masing event yang telah diserialisasi menjadi byte.

## b. URL `amqp://guest:guest@localhost:5672` sama dengan di subscriber, apa artinya?

URL `amqp://guest:guest@localhost:5672` menunjukkan alamat message broker RabbitMQ yang digunakan oleh program.

Karena URL ini sama pada `publisher` dan `subscriber`, artinya kedua program terhubung ke **message broker yang sama**, yaitu server RabbitMQ yang berjalan di komputer lokal.

Penjelasan komponennya:
- `amqp://` -> protokol yang digunakan (AMQP)
- `guest:guest` -> username dan password default RabbitMQ
- `localhost` -> server berjalan di komputer sendiri
- `5672` -> port default RabbitMQ

Dengan menggunakan URL yang sama, publisher bisa mengirim pesan ke broker, dan subscriber dapat menerima pesan dari broker tersebut

<img width="2560" height="1422" alt="Image" src="https://github.com/user-attachments/assets/831ddf6e-b60b-442c-bfd0-b74ec3ae2e83" />