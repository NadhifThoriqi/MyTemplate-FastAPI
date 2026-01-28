# 📁 Struktur Proyek Backend FastAPI

Dokumen ini menjelaskan **struktur folder dan file** pada proyek backend FastAPI yang menggunakan **SQLModel**, **JWT Authentication**, dan **Uvicorn**. Struktur ini dirancang agar kode lebih **terorganisir, mudah dipelajari, dan mudah dikembangkan**.

---

## 🗂️ Gambaran Umum Struktur Folder

```
Nama-Projek/
├── app/
│   ├── api/
│   │   └── authy.py          # Endpoint API untuk autentikasi (login & signup)
│   ├── core/
│   │   └── security.py       # Konfigurasi keamanan (JWT, hashing password)
│   ├── db/
│   │   └── session.py        # Koneksi & session database
│   ├── models/
│   │   └── user.py           # Definisi tabel database (SQLModel)
│   ├── schemas/
│   │   └── user.py           # Skema validasi data (Pydantic)
│   ├── services/
│   │   └── user_service.py   # Logika bisnis & CRUD
│   └── main.py               # Entry point aplikasi FastAPI
├── .env                      # Variabel lingkungan (database, secret key)
├── requirements.txt          # Daftar dependensi Python
└── venv/                     # Virtual environment
```

---

## 📂 Penjelasan Detail Setiap Folder & File

### 🔹 `app/`

Folder utama yang berisi seluruh kode aplikasi backend.

---

### 🔸 `app/api/`

Berisi **endpoint API** yang berhubungan langsung dengan request client.

* **`authy.py`**
  Digunakan untuk:

  * Endpoint **signup (registrasi)**
  * Endpoint **login**
  * Pengelolaan autentikasi berbasis JWT

Folder ini ideal untuk memisahkan endpoint berdasarkan fitur (auth, user, admin, dll).

---

### 🔸 `app/core/`

Berisi konfigurasi inti aplikasi.

* **`security.py`**
  Digunakan untuk:

  * Hashing & verifikasi password
  * Pembuatan dan validasi JWT
  * Pengaturan keamanan autentikasi

File ini membantu menjaga kode keamanan tetap terpusat dan konsisten.

---

### 🔸 `app/db/`

Berisi konfigurasi database.

* **`session.py`**
  Digunakan untuk:

  * Membuat engine database
  * Mengelola session database
  * Menjadi penghubung SQLModel dengan database SQL

Dengan pemisahan ini, koneksi database lebih mudah diatur dan diuji.

---

### 🔸 `app/models/`

Berisi **model database**.

* **`user.py`**
  Digunakan untuk:

  * Mendefinisikan tabel `User`
  * Menentukan kolom, tipe data, dan relasi
  * Menggunakan **SQLModel** sebagai ORM

Model di folder ini merepresentasikan struktur tabel di database.

---

### 🔸 `app/schemas/`

Berisi **skema validasi data**.

* **`user.py`**
  Digunakan untuk:

  * Validasi data request (input user)
  * Struktur response API
  * Pemisahan antara data API dan model database

Schemas membantu menjaga keamanan dan konsistensi data.

---

### 🔸 `app/services/`

Berisi **logika bisnis aplikasi**.

* **`user_service.py`**
  Digunakan untuk:

  * Operasi CRUD user
  * Logika autentikasi tambahan
  * Interaksi antara API dan database

Pendekatan ini membuat endpoint tetap bersih dan fokus pada request–response.

---

### 🔸 `app/main.py`

Merupakan **entry point aplikasi FastAPI**.

Fungsi utama:

* Inisialisasi FastAPI
* Registrasi router API
* Menjalankan server menggunakan Uvicorn

Biasanya berisi:

```python
uvicorn.run(
    "main:app",
    host="127.0.0.1",
    port=5000,
    reload=True
)
```

---

## 📄 File Pendukung

### 🔹 `.env`

Menyimpan variabel lingkungan seperti:

* URL database
* Secret key JWT
* Konfigurasi sensitif lainnya

File ini **tidak disarankan untuk di-push ke repository publik**.

---

### 🔹 `requirements.txt`

Berisi daftar library Python yang digunakan, seperti:

* fastapi
* sqlmodel
* uvicorn
* python-jose
* passlib

Digunakan untuk instalasi dependency secara cepat.

---

### 🔹 `venv/`

Virtual environment Python untuk:

* Isolasi dependensi proyek
* Menghindari konflik antar proyek

---

## 🎯 Tujuan Struktur Ini

Struktur ini dibuat untuk:

* Memisahkan tanggung jawab setiap bagian kode
* Mempermudah maintenance dan pengembangan
* Mendukung skalabilitas aplikasi
* Mudah dipahami oleh pemula maupun developer lain

---

✨ Dengan struktur ini, proyek FastAPI siap dikembangkan menjadi aplikasi backend yang aman, rapi, dan profesional.
