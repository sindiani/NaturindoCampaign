## Skenario Pengujian: Registrasi & Klaim Kupon

| ID | Fitur | Judul Test Case | Langkah Tes | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-REG-01** | Registrasi | **Positif** - Daftar Pengguna Baru | 1. Klik "Daftar Sekarang". <br> 2. NoKTP, Nama Lengkap, Alamat Domisili, Pilih Provinsi, Pilih Kota/Kabupaten, Mengenal Naturindo melalui, Usia, Agama, Pekerjaan, No whatsapp, Keluhan Kesehatan Konsumen, Order Naturindo secara, Nama Toko Marketplace Pesanan Anda, Lokasi Titik Toko Marketplace, Produk yang diorder, Masukan Kode Unik Anda <br> 3. Submit. | User berhasil terdaftar dan masuk ke Dashboard. Data tersimpan di DB. | ✅ PASS |
| **TC-REG-02** | Registrasi | **Negatif** -  Daftar Pengguna Baru | 1. Klik "Daftar Sekarang". <br> 2. NoKTP, Nama Lengkap, Alamat Domisili, Pilih Provinsi, Pilih Kota/Kabupaten, Mengenal Naturindo melalui,Usia, Agama, Pekerjaan, No whatsapp, Keluhan Kesehatan Konsumen, Order Naturindo secara, Nama Toko Marketplace Pesanan Anda, Lokasi Titik Toko Marketplace, Produk yang diorder, Masukan Kode yang perah dipakai <br> 3. Submit. <br> 2. Submit. | Muncul pesan error: "Kode sudah terdaftar". | ✅ PASS |
| **TC-REG-03** | Registrasi | **Validasi** - Input Format Password Lemah | 1. Input password hanya 3 karakter. | Sistem menolak dan meminta password minimal 8 karakter. | ✅ PASS |
| **TC-KUPON-01**| Klaim | **Negatif** - Input Kode Struk Palsu/Acak | 1. Login ke Dashboard. <br> 2. Menu "Klaim Kupon". <br> 3. Input kode asal: "XYZ123". | Sistem menolak: "Kode Transaksi tidak valid". | ✅ PASS |
| **TC-UI-01** | UI/Visual | Cek Tampilan Banner di Mobile | 1. Buka di mode iPhone 12. <br> 2. Cek tulisan "26 Desember 2024". | Teks tanggal tidak terpotong dan tombol "Daftar" mudah diklik. | ✅ PASS |
