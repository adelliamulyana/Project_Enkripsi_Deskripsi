# Project_Enkripsi_Dekripsi
# Enkripsi dan Dekripsi Pesan Menggunakan Grup Permutasi (S_n)

Repositori ini berisi implementasi algoritma kriptografi klasik berbasis **Grup Permutasi (S_n)** menggunakan bahasa pemrograman **Python**. Proyek ini dibuat untuk mensimulasikan pengamanan informasi melalui proses pengacakan posisi karakter per blok berbasis teori aljabar abstrak.

---

## Latar Belakang

Perkembangan teknologi informasi dan komunikasi yang pesat mempermudah proses pertukaran pesan secara digital. Namun, pengiriman pesan melalui jaringan publik sangat rentan terhadap ancaman penyadapan (*eavesdropping*) atau pengubahan isi pesan oleh pihak yang tidak berwenang. 

Untuk meminimalisir risiko tersebut, diperlukan mekanisme pengamanan data melalui **kriptografi**, yaitu proses enkripsi (mengubah teks asli menjadi kode acak) dan dekripsi (mengembalikan kode acak menjadi teks asli). Dalam proyek ini, pendekatan struktur aljabar khususnya **Grup Simetri/Permutasi S_n** dimanfaatkan sebagai dasar pembentukan kunci rahasia untuk mengacak dan mengembalikan urutan karakter dalam pesan.

---

## Masalah

Proyek ini bertujuan untuk menjawab beberapa permasalahan utama:
1. **Bagaimana proses enkripsi pesan** menggunakan konsep grup permutasi S_n untuk mengamankan informasi dari pihak yang tidak berwenang?
2. **Bagaimana proses dekripsi pesan** menggunakan invers dari permutasi S_n agar pesan dapat dibaca kembali oleh penerima yang sah?
3. **Bagaimana mengimplementasikan algoritma enkripsi dan dekripsi tersebut** ke dalam bentuk program komputer otomatis berbasis Python?

---

## 🛠️ Tools

Proyek ini dikembangkan menggunakan bahasa dan pustaka berikut:

- **Bahasa Pemrograman:** Python 
- **Pustaka Bawaan (Standard Library):**
  - `random`: Untuk menghasilkan permutasi acak (kunci) dan menentukan panjang blok secara dinamis.
- **Teks Editor / Environment:** Visual Studio Code (VS Code)

---

## 🔄 Workflow (Alur Kerja)

Alur kerja sistem enkripsi dan dekripsi berbasis permutasi ini terbagi menjadi dua proses utama:
### 1. Alur Enkripsi:
1. **Input Teks:** Memasukkan teks asli (*plaintext*).
2. **Pra-pemrosesan Teks:** Mengubah semua karakter spasi menjadi simbol `#` untuk menjaga integritas posisi teks.
3. **Pembentukan Blok & Padding:** Membagi teks menjadi blok-blok berukuran n (antara 2 hingga 10 karakter secara acak). Jika panjang blok terakhir kurang dari n, ditambahkan karakter *padding* `$`.
4. **Permutasi (Kunci):** Menghasilkan elemen permutasi θ secara acak.
5. **Transformasi:** Mengaplikasikan permutasi θ pada setiap blok untuk menghasilkan teks acak (*ciphertext*).

### 2. Alur Dekripsi:
1. **Input Ciphertext & Kunci:** Memasukkan *ciphertext* serta kunci permutasi θ yang disepakati.
2. **Invers Kunci:** Menghitung invers dari permutasi θ^-1.
3. **Restorasi Blok:** Membagi *ciphertext* menjadi blok-blok berukuran $n$ dan mengaplikasikan θ^-1 pada setiap blok.
4. **Pembersihan Teks:** Menghapus simbol *padding* `$` dan mengembalikan simbol `#` menjadi karakter spasi hingga diperoleh kembali *plaintext* asli.

---

## 💡 Temuan

Berdasarkan implementasi dan pengujian program, diperoleh beberapa temuan utama:

1. **Efektivitas Pengacakan:** Penggunaan grup permutasi S_n secara otomatis mampu mengacak urutan karakter dengan baik sehingga menyulitkan pihak ketiga (*eavesdropper*) dalam membaca isi pesan asli tanpa memiliki kunci permutasi.
2. **Proteksi Permutasi Identitas:** Pembuatan kunci permutasi acak perlu dilengkapi pengondisian untuk menghindari terbentuknya **permutasi identitas** (permutasi yang tidak mengubah posisi elemen), sebab jika permutasi identitas terpilih, *ciphertext* yang dihasilkan akan persis sama dengan *plaintext*.
3. **Pentingnya Parameter Dinamis:** Penggunaan ukuran blok acak (S_n>=2) dan penambahan karakter *padding* (`$`) terbukti menjaga kestabilan proses enkripsi-dekripsi untuk kalimat dengan berbagai variasi panjang kata.
4. **Presisi Dekripsi dengan Invers Matriks/Fungsi:** Sifat matematis invers fungsi pada grup permutasi (θ∘θ^(-1)=e) menjamin pesan yang didekripsi 100% presisi dan identik dengan *plaintext* awal.
