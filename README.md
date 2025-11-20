# Naturindo Customer Reward Platform - QA Project

Repositori ini mendokumentasikan proses Quality Assurance untuk platform "Beli Jamu Dapat Hadiah Umroh". Sistem ini memungkinkan pelanggan menukarkan bukti pembelian menjadi kupon undian berhadiah.

### 🎯 Fokus Pengujian (Test Objectives)
Karena sistem ini melibatkan undian dan data pelanggan, fokus utama pengujian adalah:
1.  **User Registration Flow:** Memastikan validasi data diri (Nama, No HP, KTP) berjalan ketat untuk mencegah akun palsu.
2.  **Coupon Redemption Logic:** Memvalidasi mekanisme klaim kupon (Input Kode Struk/Upload Struk) agar tidak ada kode ganda (*double claim*).
3.  **Mobile Responsiveness:** Memastikan banner promosi dan tombol "Daftar" terlihat jelas di layar HP (mengingat target user umum).
4.  **Performance:** Memastikan website tidak *down* saat trafik tinggi di akhir periode undian.

### 🛠️ Tools & Tech
* **Manual Testing:** Functional & Usability Testing.
* **API Testing:** Validasi endpoint Pendaftaran & Klaim Kupon.
* **JMeter:** Load testing simulasi 100 user mendaftar bersamaan.
