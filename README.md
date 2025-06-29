Deskripsi
Dessert Clicker adalah sebuah aplikasi Android sederhana yang dibangun untuk mendemonstrasikan konsep-konsep dasar pengembangan Android modern menggunakan Kotlin dan Jetpack Compose. Aplikasi ini merupakan sebuah game clicker di mana pengguna mengetuk (klik) gambar hidangan penutup (dessert) untuk mendapatkan "pendapatan" dan meningkatkan jumlah hidangan yang terjual. Seiring berjalannya permainan, hidangan penutup yang ditampilkan akan berubah menjadi lebih mahal.

Aplikasi ini juga mengilustrasikan cara mengelola state (data) dalam Jetpack Compose, menangani interaksi pengguna, serta menggunakan komponen UI dasar dari Material 3.

Fitur Utama
Gameplay Sederhana: Klik pada gambar hidangan penutup untuk meningkatkan pendapatan dan jumlah penjualan.

Sistem Progresi: Hidangan penutup baru akan muncul secara otomatis seiring dengan bertambahnya jumlah hidangan yang terjual.

Pelacakan Skor: Aplikasi menampilkan total pendapatan (revenue) dan jumlah hidangan yang terjual (desserts sold) secara real-time.

Fungsi Berbagi (Share): Terdapat tombol share di AppBar untuk membagikan pencapaian (total penjualan dan pendapatan) ke aplikasi lain melalui Intent.

Penyimpanan State: Skor dan progres permainan akan tetap tersimpan bahkan setelah layar diputar (perubahan konfigurasi), berkat penggunaan rememberSaveable.

Logging Siklus Hidup (Lifecycle): Terdapat log di Logcat untuk setiap tahapan siklus hidup Activity (onCreate, onStart, onPause, onDestroy, dll.), yang sangat berguna untuk tujuan pembelajaran dan debugging.

Cara Kerja & Detail Teknis
Aplikasi ini dibangun sepenuhnya menggunakan Jetpack Compose, toolkit UI modern dari Google untuk membangun antarmuka pengguna native.

Manajemen State:
State utama seperti revenue, dessertsSold, dan data hidangan penutup yang sedang ditampilkan dikelola di dalam Composable DessertClickerApp menggunakan rememberSaveable { mutableStateOf(...) }. Penggunaan rememberSaveable memastikan bahwa data tidak hilang saat terjadi perubahan konfigurasi, seperti rotasi layar.

Logika Permainan:
Logika inti berada di dalam lambda onDessertClicked pada DessertClickerScreen. Setiap kali pengguna mengklik gambar dessert:

revenue diperbarui dengan menambahkan harga dessert saat ini.

dessertsSold bertambah satu.

Fungsi determineDessertToShow() dipanggil. Fungsi ini memeriksa jumlah total dessert yang telah terjual dan menentukan dessert mana yang seharusnya ditampilkan selanjutnya berdasarkan daftar yang telah diurutkan (Datasource.dessertList).

Struktur UI:

Scaffold: Digunakan sebagai kerangka layout utama yang menyediakan slot untuk topBar dan konten utama.

DessertClickerAppBar: Composable kustom untuk menampilkan judul aplikasi dan tombol share.

DessertClickerScreen: Menampilkan layout utama permainan, termasuk gambar latar belakang, gambar dessert yang bisa diklik, dan informasi transaksi.

TransactionInfo: Composable yang menampilkan total pendapatan dan jumlah dessert terjual di bagian bawah layar.

Struktur File
MainActivity.kt adalah file utama yang berisi seluruh logika dan komponen UI aplikasi ini. Di dalamnya terdapat:

MainActivity: Kelas Activity yang menjadi titik masuk aplikasi. Di sini, siklus hidup (lifecycle) Android dicatat ke Logcat.

DessertClickerApp: Composable utama yang menampung semua state dan logika UI.

Composable Pendukung: Seperti DessertClickerScreen, DessertClickerAppBar, dan TransactionInfo yang membentuk antarmuka pengguna.

Fungsi Helper:

determineDessertToShow(): Menentukan dessert mana yang akan ditampilkan berdasarkan progres.

shareSoldDessertsInformation(): Membuat dan menjalankan Intent untuk berbagi teks.

Teknologi yang Digunakan
Bahasa: Kotlin

UI Toolkit: Jetpack Compose

Desain: Material 3

Arsitektur: UI State Management dengan mutableStateOf dan rememberSaveable.

Dasar Android: Activity Lifecycle, Intent.

Cara Menjalankan Proyek
Buka proyek ini menggunakan Android Studio.

Pastikan semua dependensi Gradle telah tersinkronisasi.

Jalankan aplikasi pada emulator Android atau perangkat fisik.

Klik pada gambar dessert untuk bermain dan perhatikan Logcat untuk melihat output dari siklus hidup Activity.
