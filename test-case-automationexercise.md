# Test Case — Automation Exercise

| Field | Keterangan |
| --- | --- |
| **Nama Proyek** | Automation Exercise (E-Commerce Practice Site) |
| **URL** | https://automationexercise.com/ |
| **Modul** | End-to-End Functional (Register, Login, Cart, Contact, Product, Subscription) |
| **Jumlah Test Case** | 10 (TC-001 s/d TC-010) |

**Keterangan kolom `Jenis`**

- **Positive** → skenario dengan input/flow valid, sistem diharapkan sukses.
- **Negative** → skenario dengan input tidak valid, sistem diharapkan menolak dan menampilkan pesan error.

---

## Tabel Test Case

| ID | Skenario | Step | Jenis | Expected |
| --- | --- | --- | --- | --- |
| **TC-001** | Register User (pendaftaran akun baru) | 1. Buka `https://automationexercise.com/`<br>2. Klik menu **Signup / Login**<br>3. Pada section *New User Signup!*, isi **Name** = `QA Tester`<br>4. Isi **Email Address** = email baru yang belum terdaftar<br>5. Klik tombol **Signup**<br>6. Verifikasi H2 **ENTER ACCOUNT INFORMATION** tampil<br>7. Isi *Title*, **Password** = `P@ssw0rd123`, **Date of Birth**<br>8. Centang **Sign up for our newsletter!** dan **Receive special offers**<br>9. Isi **First name**, **Last name**, **Company**, **Address**, **Country**, **State**, **City**, **Zipcode**, **Mobile Number**<br>10. Klik tombol **Create Account**<br>11. Verifikasi **ACCOUNT CREATED!** tampil<br>12. Klik tombol **Continue**<br>13. Verifikasi header menampilkan **Logged in as QA Tester**<br>14. Klik **Delete Account**<br>15. Verifikasi **ACCOUNT DELETED!** tampil, lalu klik **Continue** | Positive | 1. Halaman Signup/Login terbuka (`/login`)<br>2. Form *New User Signup!* tampil dengan field Name & Email<br>3. Redirect ke `/signup` dengan H2 **ENTER ACCOUNT INFORMATION** dan field **Name** ter-prefill `QA Tester`<br>4. Form Address Information tampil lengkap<br>5. Redirect ke `/account_created` dengan H2 **ACCOUNT CREATED!** dan teks *Congratulations! Your new account has been successfully created!*<br>6. Setelah **Continue**, user login otomatis dan header menampilkan **Logged in as QA Tester**<br>7. Redirect ke `/delete_account` dengan H2 **ACCOUNT DELETED!** dan teks *Your account has been permanently deleted!* |
| **TC-002** | Login User dengan email dan password yang benar | 1. Buka `https://automationexercise.com/`<br>2. Klik menu **Signup / Login**<br>3. Verifikasi H2 **Login to your account** tampil<br>4. Isi **Email Address** dengan email akun yang sudah terdaftar<br>5. Isi **Password** dengan password yang benar<br>6. Klik tombol **Login**<br>7. Verifikasi header setelah login | Positive | 1. Halaman `/login` terbuka<br>2. H2 **Login to your account** tampil<br>3. Login berhasil, redirect ke halaman Home (`/`)<br>4. Header menampilkan **Logged in as QA Tester**<br>5. Menu **Logout** dan **Delete Account** muncul, menu **Signup / Login** hilang |
| **TC-003** | Login User dengan email dan password yang salah | 1. Buka `https://automationexercise.com/login`<br>2. Isi **Email Address** = `salah@email.com`<br>3. Isi **Password** = `salah123`<br>4. Klik tombol **Login**<br>5. Perhatikan pesan yang muncul di form login | Negative | 1. Login **gagal** — user tidak diarahkan ke halaman Home<br>2. Tetap berada di `/login`<br>3. Muncul pesan error: **Your email or password is incorrect!**<br>4. Header **tidak** menampilkan *Logged in as ...* |
| **TC-004** | Logout User | 1. Login terlebih dahulu dengan akun valid (lihat TC-002)<br>2. Verifikasi header menampilkan **Logged in as QA Tester**<br>3. Klik menu **Logout**<br>4. Verifikasi halaman yang tampil setelah logout | Positive | 1. Logout berhasil<br>2. Redirect ke halaman Login (`/login`)<br>3. H2 **Login to your account** tampil kembali<br>4. Menu **Signup / Login** muncul lagi, menu **Logout** hilang<br>5. Session user berakhir (akses halaman member tidak lagi sebagai user login) |
| **TC-005** | Register User dengan email yang sudah terdaftar | 1. Buka `https://automationexercise.com/login`<br>2. Pada section *New User Signup!*, isi **Name** = `QA Tester`<br>3. Isi **Email Address** dengan email yang **sudah pernah didaftarkan**<br>4. Klik tombol **Signup**<br>5. Perhatikan pesan error di bawah form signup | Negative | 1. Pendaftaran **ditolak** — user tidak diarahkan ke form `ENTER ACCOUNT INFORMATION`<br>2. Tetap berada di halaman signup (`/signup`)<br>3. Muncul pesan error: **Email Address already exist!**<br>4. Tidak ada akun baru yang terbuat |
| **TC-006** | Contact Us Form (kirim pesan ke customer service) | 1. Buka `https://automationexercise.com/contact_us`<br>2. Verifikasi H2 **GET IN TOUCH** tampil<br>3. Isi **Name** = `QA Tester`<br>4. Isi **Email** = `qa.tester@mailinator.com`<br>5. Isi **Subject** = `Test Subject`<br>6. Isi **Your Message Here** = `Pesan testing otomasi.`<br>7. *(Opsional)* Upload file pada **Upload File**<br>8. Klik tombol **Submit**<br>9. Klik **OK** pada dialog konfirmasi browser<br>10. Verifikasi pesan sukses | Positive | 1. Halaman `/contact_us` terbuka dengan H2 **GET IN TOUCH**<br>2. Saat **Submit** diklik, muncul native dialog browser: **Press OK to proceed!**<br>3. Setelah **OK**, halaman menampilkan pesan sukses: **Success! Your details have been submitted successfully.**<br>4. Tombol **Home** tersedia untuk kembali ke halaman utama |
| **TC-007** | Verify Test Cases Page (verifikasi halaman daftar test case) | 1. Buka `https://automationexercise.com/`<br>2. Klik menu **Test Cases**<br>3. Verifikasi URL dan heading halaman<br>4. Verifikasi daftar test case yang tampil<br>5. Klik salah satu test case untuk expand detail step-nya | Positive | 1. Halaman navigasi ke `/test_cases`<br>2. H2 **TEST CASES** tampil<br>3. Daftar test case tampil berurutan mulai dari **Test Case 1: Register User** hingga **Test Case 26**<br>4. Setiap item dapat di-expand (accordion) dan menampilkan detail langkah<br>5. Tidak ada error / halaman blank |
| **TC-008** | Verify All Products dan Product Detail Page | 1. Buka `https://automationexercise.com/`<br>2. Klik menu **Products**<br>3. Verifikasi halaman **ALL PRODUCTS** tampil<br>4. Verifikasi daftar produk tampil lengkap<br>5. Klik tombol/link **View Product** pada produk pertama (**Blue Top**)<br>6. Verifikasi detail produk yang tampil | Positive | 1. Halaman navigasi ke `/products`<br>2. H2 **ALL PRODUCTS** tampil beserta daftar produk (nama, harga, tombol *Add to cart* & *View Product*)<br>3. Redirect ke `/product_details/1`<br>4. Detail produk tampil lengkap: nama **Blue Top**, kategori **Women > Tops**, harga **Rs. 500**, **Availability: In Stock**, **Condition: New**, **Brand: Polo**<br>5. Field **Quantity**, tombol **Add to cart**, dan section **Write Your Review** tersedia |
| **TC-009** | Search Product | 1. Buka `https://automationexercise.com/products`<br>2. Verifikasi H2 **ALL PRODUCTS** tampil<br>3. Isi field search dengan keyword `Tshirt`<br>4. Klik tombol **Search** (icon magnifier)<br>5. Verifikasi hasil pencarian<br>6. Verifikasi daftar produk yang muncul relevan | Positive | 1. Halaman `/products` terbuka<br>2. URL berubah menjadi `/products?search=Tshirt`<br>3. H2 **SEARCHED PRODUCTS** tampil<br>4. Menampilkan produk relevan dengan keyword, antara lain: **Pure Cotton V-Neck T-Shirt**, **Green Side Placket Detail T-Shirt**, **Premium Polo T-Shirts**, **Pure Cotton Neon Green Tshirt**, **GRAPHIC DESIGN MEN T SHIRT - BLUE**<br>5. Setiap hasil memiliki harga dan tombol **Add to cart** / **View Product** |
| **TC-010** | Verify Subscription di halaman Home | 1. Buka `https://automationexercise.com/`<br>2. Scroll ke bagian paling bawah halaman<br>3. Verifikasi heading **SUBSCRIPTION** tampil<br>4. Isi field email dengan `subscriber@mailinator.com`<br>5. Klik tombol panah / **Subscribe**<br>6. Verifikasi pesan sukses yang muncul | Positive | 1. Halaman Home terbuka<br>2. Section footer dengan heading **SUBSCRIPTION** tampil<br>3. Field email dan tombol subscribe dapat diakses<br>4. Setelah subscribe, muncul pesan sukses: **You have been successfully subscribed!**<br>5. Field email ter-reset / pesan sukses tetap tampil tanpa reload penuh |

---

## Ringkasan

| Jenis | Jumlah | ID |
| --- | --- | --- |
| Positive | 8 | TC-001, TC-002, TC-004, TC-006, TC-007, TC-008, TC-009, TC-010 |
| Negative | 2 | TC-003, TC-005 |
| **Total** | **10** | TC-001 s/d TC-010 |

---
