**Dokumentasi pengujian endpoint (URL) backend**
# Laporan Pengujian API (API Test Report)

**Project:** Naturindo Customer Reward Platform
**Tools:** Postman & Swagger
**Test Date:** November 2024
**Base URL:** `https://api-dev.naturindo-reward.com/v1` 

---

## 1. Ringkasan Eksekusi (Execution Summary)

Pengujian dilakukan untuk memvalidasi integritas data antara aplikasi Frontend (Mobile/Web) dan Server Backend, khususnya pada fitur krusial seperti **Registrasi** dan **Klaim Kupon**.

| Modul API | Total Endpoint | Pass | Fail | Cakupan Tes |
| :--- | :---: | :---: | :---: | :--- |
| **Auth (Registrasi/Login)** | 3 | 3 | 0 | Validasi Token & Format Data |
| **Transaction (Klaim)** | 2 | 2 | 0 | Validasi Kode Unik & Duplikasi |
| **Profile (User Data)** | 1 | 1 | 0 | Validasi Data Poin |

---

## 2. Detail Skenario Pengujian (Test Scenarios)

Berikut adalah sampel *Request* dan *Response* dari pengujian yang dilakukan.

### A. Fitur Registrasi User (Auth)
**Endpoint:** `POST /auth/register`
**Tujuan:** Mendaftarkan user baru dan memastikan validasi nomor WA.

**Request Body (JSON):**
```json
{
  "full_name": "Budi Santoso",
  "whatsapp_number": "081234567890",
  "password": "SecurePassword123!",
  "city_id": 105
}
Scenario 1: Registrasi Berhasil (Positive)
    Status Code: 201 Created
    Response: User ID terbentuk.

Scenario 2: Nomor WA Sudah Terdaftar (Negative)
    Status Code: 400 Bad Request
    Response Body:{
      "status": "error",
      "message": "Nomor WhatsApp sudah terdaftar. Silakan Login."
    }

B. Fitur Login & Token (Auth)
    Endpoint: POST /auth/login Tujuan: Mendapatkan Access Token (Bearer Token) untuk mengakses fitur klaim.
    Request Body:
    JSON
    {
      "whatsapp_number": "081234567890",
      "password": "SecurePassword123!"
    }
Scenario: Login Sukses
    Status Code: 200 OK
    Response Body:
    JSON
    {
      "status": "success",
      "data": {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
        "token_type": "Bearer",
        "expires_in": 3600
      }
}
Fitur Klaim Kupon (Core Logic)
    Endpoint: POST /coupon/claim Header: Authorization: Bearer {token} Tujuan: Menukarkan kode struk transaksi menjadi kupon undian.
    Request Body:
    JSON
    {
      "transaction_code": "NAT-INV-2024-001",
      "store_name": "Apotek Sehat Jaya",
      "purchase_amount": 150000
    }
Scenario 1: Klaim Berhasil
    Status Code: 200 OK
    Response Body:
    JSON
    {
      "status": "success",
      "message": "Klaim berhasil. Anda mendapatkan 1 Kupon Undian.",
      "coupon_id": "CUP-882910"
    }
Scenario 2: Kode Transaksi Sudah Dipakai (Fraud Prevention)
    Status Code: 409 Conflict
    Response Body:
    JSON
    {
      "status": "fail",
      "code": "DUPLICATE_TRANSACTION",
      "message": "Kode transaksi ini sudah pernah diklaim sebelumnya."
    }
