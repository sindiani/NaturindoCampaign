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
