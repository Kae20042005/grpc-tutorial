# Module 08 Reflection

1. Unary merupakan RPC method di mana client mengirim satu request maka akan  mendapatkan satu response, cocok digunakan
untuk CRUD dasar dan authentication. Server Streaming merupakan RPC method di mana client mengirim satu request dan
mendapat stream response dari server, cocok digunakan untuk logs. Bidirectional Streaming merupakan PC method di mana
client dan server dapat mengirim stream dari message secara independen, cocok digunakan untuk Chat apps.
2. * Authentication: Penggunaan JWTs untuk validasi identitas
   * Authorization: Penerapan kontrol akses yang rinci dalam service
   * Data Encryption: Menggunakan TLS
3. * State Management: Menyimpan koneksi aktif pengguna. 
   * Backpressure: Mengelola aliran data agar tidak overload. 
   * Error Propagation: Tangani error sisi klien/server secara terpisah.
4. Kelebihan & Kekurangan ReceiverStream<br>
|Kelebihan|Kekurangan|
|---------|----------|
|Mudah digunakan dengan channel async|Tidak ada pengaturan buffering otomatis|
|Dekoupling antara produsen dan konsumen data|Kurang cocok untuk beban performa tinggi|
|Sederhana dan cocok untuk servis ringan|Tidak seefisien solusi custom dengan kontrol penuh|
5. * Pemisahan setiap layanan
   * Menggunakan modul common untuk tipe & utilitas bersama
   * Letakkan tipe file proto di crate tersendiri agar mudah diubah & dibagi
   * Gunakan clean architecture
6. * Penambahan validasi input
   * Penyimpanan data ke database
   * Pencatatan log
7. Pengaruh gPRC terhadap arsitektur sistem terdistribusi
|Kelebihan|Kekurangan|
|---------|----------|
|Dukungan multi-bahasa via Protobuf|Tidak semudah REST dalam debugging|
|Performa tinggi & dukungan streaming|Perlu tool tambahan|
|Kontrak API eksplisit & kuat dari `.proto`|Dukungan langsung dari browser terbatas (perlu gPRC-Web)|
8. Perbandingan HTTP/2, Http/1.1, Websocket
|Protokol|Kelebihan|Kekurangan|
|--------|---------|----------|
|HTTP/2|Multiplexing, efisiensi tinggi|Lebih kompleks|
|HTTP/1.1|Lebih sederhana, kompatibel luas|Tidak bisa multiplex secara native|
|WebSocket|Full-duplex, cocok untuk real-time|Tidak seformal gPRC (kurang kontrak API)|
9. Metode request-response dalam REST tidak berjalan secara realtime di mana pertama request diberikan lalu ada response
sebagai balasan. Sedangkan pada metode bidirectional streaming dalam gRPC, komunikasi dapat berjalan secara dua arah dan
komunikasi terjadi secara real-time.
10. Perbandingan schema-based gRPC dengan schema-less JSON dalam REST API
|gRPC (protobuf)|REST (JSON)|
|---------------|-----------|
|Tipe data ketat & validasi otomatis|Fleksibel dan mudah diuji secara manual|
|Kontrak API dengan `.proto`|Tidak punya format kontrak eksplisit secara default|
|Cocok untuk integrasi skala besar & lintas bahasa|Cocok untuk API publik|