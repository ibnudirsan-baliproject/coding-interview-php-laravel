# Coding Interview - PHP Laravel Developer

## **Catatan**
- Dilarang menggunakan chatGPT dan AI sejenisnya.
- Dibolehkan membuka dokumentasi Laravel atau website programming yang lainnya
- Dibolehkan membukan situs pencarian seperti google dan sejenisnya.
- Dibolehkan membuka project portofolio yang sudah ada sebagai referensi.

## Deskripsi
Buatlah sebuah API tanpa autentikasi yang menggunakan model **Employee** dengan tabel `employees`. API ini harus menyediakan fitur CRUD dasar untuk mengelola data karyawan.

### **Struktur Tabel Employee**
Tabel `employees` memiliki kolom sebagai berikut:
- `id` (integer, primary key, auto-increment)
- `fullname` (string, required)
- `email` (string, unique, required)
- `mobilephone` (string, required)
- `date_of_birth` (date, required)
- `address` (text, required)

### **Endpoint Employee**
1. `[GET] /api/employee` - Mendapatkan daftar semua karyawan.
   **Response JSON:**
   ```json
   {
       "status": "success",
       "data": [
           {
               "id": 1,
               "fullname": "John Doe",
               "email": "john@example.com",
               "mobilephone": "08123456789",
               "date_of_birth": "1990-01-01",
               "address": "Jl. Contoh No.1"
           }
       ]
   }
   ```

2. `[POST] /api/employee` - Menambahkan data karyawan baru.
   **Response JSON:**
   ```json
   {
       "status": "success",
       "message": "Employee added successfully",
       "data": {
           "id": 2,
           "fullname": "Jane Smith",
           "email": "jane@example.com",
           "mobilephone": "08129876543",
           "date_of_birth": "1995-05-15",
           "address": "Jl. Contoh No.2"
       }
   }
   ```

3. `[DELETE] /api/employee/{id}` - Menghapus data karyawan berdasarkan `employee_id`.
   **Response JSON:**
   ```json
   {
       "status": "success",
       "message": "Employee deleted successfully"
   }
   ```

4. `[GET] /api/employee/{id}` - Mendapatkan informasi satu karyawan berdasarkan `employee_id`.
   **Response JSON:**
   ```json
   {
       "status": "success",
       "data": {
           "id": 1,
           "fullname": "John Doe",
           "email": "john@example.com",
           "mobilephone": "08123456789",
           "date_of_birth": "1990-01-01",
           "address": "Jl. Contoh No.1"
       }
   }
   ```

---

## **Nilai Tambahan (Opsional)**
Jika dikerjakan, ini akan menjadi nilai tambah dalam evaluasi.

### **Relasi One-to-Many dengan Experience**
Tambahkan model **Experience** dengan tabel `experiences`, yang memiliki hubungan **one-to-many** dengan tabel `employees`. Setiap karyawan dapat memiliki banyak pengalaman kerja.

### **Struktur Tabel Experience**
Tabel `experiences` memiliki kolom sebagai berikut:
- `id` (integer, primary key, auto-increment)
- `employee_id` (integer, foreign key ke `employees.id`, required)
- `company_name` (string, required)
- `job_title` (string, required)
- `start_date` (date, required)
- `end_date` (date, optional, bisa `NULL` jika masih bekerja)
- `job_description` (text, required)

### **Endpoint Experience**
1. `[POST] /api/experience` - Menambahkan pengalaman kerja untuk karyawan.
   **Response JSON:**
   ```json
   {
       "status": "success",
       "message": "Experience added successfully",
       "data": {
           "id": 1,
           "fullname": "John Doe",
           "experience": [
               {
                   "id": 1,
                   "company_name": "Google",
                   "job_title": "Backend Developer",
                   "start_date": "2018-06-01",
                   "end_date": "2021-05-31",
                   "job_description": "Worked on scalable backend services."
               }
           ]
       }
   }
   ```

2. `[GET] /api/experience/{employee_id}` - Mendapatkan daftar pengalaman kerja berdasarkan `employee_id` dengan relasi ke tabel employees.
   **Response JSON:**
   ```json
   {
       "status": "success",
       "data": {
           "id": 1,
           "fullname": "John Doe",
           "experience": [
               {
                   "id": 1,
                   "company_name": "Google",
                   "job_title": "Backend Developer",
                   "start_date": "2018-06-01",
                   "end_date": "2021-05-31",
                   "job_description": "Worked on scalable backend services."
               }
           ]
       }
   }
   ```

---
