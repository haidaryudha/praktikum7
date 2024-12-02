# praktikum7

## 1. **Deklarasi Variabel `data_mahasiswa`**

```python
data_mahasiswa = []
```

- Program dimulai dengan mendeklarasikan **list kosong** yang diberi nama `data_mahasiswa`. List ini akan berfungsi sebagai wadah untuk menyimpan data mahasiswa. 
- Setiap **data mahasiswa** disimpan dalam bentuk **dictionary** yang terdiri dari dua elemen utama: `nama` dan `nilai`. Data ini akan dimasukkan ke dalam list tersebut saat pengguna menambahkan mahasiswa baru.
  
Contoh data yang disimpan dalam `data_mahasiswa` setelah beberapa input adalah:

```python
[{"nama": "Alice", "nilai": 85.0}, {"nama": "Bob", "nilai": 90.5}]
```

---

## 2. **Fungsi `tambah()` - Menambahkan Data Mahasiswa**

```python
def tambah():
    print("-" * 42)
    nama = input("1. Masukkan nama mahasiswa: ")
    nilai = float(input("2. Masukkan nilai mahasiswa: "))
    print("-" * 42)
    data_mahasiswa.append({"nama": nama, "nilai": nilai})
    print("=" * 42)
    print("|    --- Data berhasil ditambahkan! ---  |")
    print("=" * 42)
```

Fungsi ini bertugas untuk menambahkan data mahasiswa baru ke dalam list `data_mahasiswa`. Penjelasannya adalah sebagai berikut:

- **Langkah 1**: Program akan menampilkan garis horizontal (`"-" * 42`) untuk memberi pemisah antara tampilan data yang akan dimasukkan dengan tampilan sebelumnya.
- **Langkah 2**: Pengguna diminta untuk **memasukkan nama mahasiswa**. Nama ini akan disimpan dalam variabel `nama`.
- **Langkah 3**: Setelah itu, program meminta pengguna untuk memasukkan **nilai mahasiswa**. Nilai yang dimasukkan akan diubah menjadi tipe data `float` untuk mengakomodasi nilai desimal (misalnya, 85.5).
- **Langkah 4**: Data yang terdiri dari nama dan nilai mahasiswa akan disimpan dalam sebuah dictionary, kemudian ditambahkan ke dalam list `data_mahasiswa` menggunakan metode `append()`.
- **Langkah 5**: Setelah data berhasil ditambahkan, program menampilkan pesan konfirmasi bahwa data telah berhasil ditambahkan.

Contoh hasil setelah fungsi ini dijalankan:
```
1. Masukkan nama mahasiswa: Alice
2. Masukkan nilai mahasiswa: 85
Data berhasil ditambahkan!
```

---

## 3. **Fungsi `tampilkan()` - Menampilkan Data Mahasiswa**

```python
def tampilkan():
    if not data_mahasiswa:
        print()
        print("=" * 34)
        print("--- Belum ada data mahasiswa ---")
        print("=" * 34)
    else:
        print()
        print("--- Daftar Nilai Mahasiswa A.3 ---")
        print("=" * 34)
        print("| NO |       NAMA       | NILAI |")
        print("-" * 33)
        for i, mahasiswa in enumerate(data_mahasiswa, 1):
            print(f"|{i:3}.| {mahasiswa['nama']:16} | {mahasiswa['nilai']:6}|")
        print("=" * 34)
```

Fungsi ini digunakan untuk **menampilkan semua data mahasiswa** yang telah disimpan dalam list `data_mahasiswa`. Berikut adalah penjelasannya:

- **Langkah 1**: Program pertama-tama memeriksa apakah **list `data_mahasiswa` kosong** menggunakan kondisi `if not data_mahasiswa`. Jika list kosong, program akan menampilkan pesan bahwa belum ada data mahasiswa.
- **Langkah 2**: Jika ada data mahasiswa, program akan menampilkan daftar mahasiswa dalam bentuk **tabel** yang terdiri dari:
  - **Nomor urut** (dengan `enumerate(data_mahasiswa, 1)` yang memberikan nomor mulai dari 1).
  - **Nama mahasiswa** yang diambil dari dictionary (`mahasiswa['nama']`).
  - **Nilai mahasiswa** yang diambil dari dictionary (`mahasiswa['nilai']`).
  
Program menggunakan format **tabel** agar data lebih mudah dibaca dengan kolom yang teratur.

Contoh output setelah beberapa data mahasiswa dimasukkan:
```
Daftar Nilai Mahasiswa A.3
------------------------------------
| NO |       NAMA       | NILAI |
------------------------------------
|  1 | Alice            |  85.0 |
|  2 | Bob              |  90.5 |
------------------------------------
```

---

## 4. **Fungsi `hapus(nama)` - Menghapus Data Mahasiswa Berdasarkan Nama**

```python
def hapus(nama):
    global data_mahasiswa
    data_mahasiswa = [m for m in data_mahasiswa if m['nama'] != nama]
    print("=" * 65)
    print(f"--- Data mahasiswa dengan nama '{nama}' telah dihapus! ---")
    print("=" * 65)
```

Fungsi ini digunakan untuk **menghapus data mahasiswa** berdasarkan nama yang diberikan sebagai parameter. Berikut adalah penjelasannya:

- **Langkah 1**: Fungsi menerima parameter `nama`, yaitu nama mahasiswa yang ingin dihapus.
- **Langkah 2**: Program menggunakan **list comprehension** untuk memfilter data mahasiswa. List comprehension ini akan membuat list baru yang berisi semua mahasiswa kecuali yang memiliki nama yang sesuai dengan parameter `nama`. Dengan cara ini, mahasiswa dengan nama yang dimasukkan akan dihapus dari list `data_mahasiswa`.
  
Contoh: 
Jika data mahasiswa adalah `[{"nama": "Alice", "nilai": 85}, {"nama": "Bob", "nilai": 90}]`, dan pengguna menghapus data mahasiswa dengan nama `"Alice"`, maka list `data_mahasiswa` yang baru akan menjadi:
```
[{"nama": "Bob", "nilai": 90}]
```

- **Langkah 3**: Setelah data berhasil dihapus, program akan menampilkan pesan konfirmasi bahwa data dengan nama tersebut telah dihapus.

---

## 5. **Fungsi `ubah(nama)` - Mengubah Nilai Mahasiswa Berdasarkan Nama**

```python
def ubah(nama):
    for mahasiswa in data_mahasiswa:
        if mahasiswa['nama'] == nama:
            mahasiswa['nilai'] = float(input(f"2. Masukkan nilai baru untuk {nama}: "))
            print("-" * 55)
            print("=" * 55)
            print("|            --- Data berhasil diubah! ---            |")
            print("=" * 55)
            return
    print(f"Data mahasiswa dengan nama '{nama}' tidak ditemukan.")
```

Fungsi ini digunakan untuk **mengubah nilai mahasiswa** berdasarkan nama. Berikut penjelasannya:

- **Langkah 1**: Fungsi ini menerima parameter `nama`, yaitu nama mahasiswa yang nilai nya ingin diubah.
- **Langkah 2**: Program melakukan iterasi melalui semua data mahasiswa dalam list `data_mahasiswa`. Jika nama mahasiswa yang ditemukan sesuai dengan parameter `nama`, maka program akan meminta pengguna untuk **memasukkan nilai baru** untuk mahasiswa tersebut.
- **Langkah 3**: Nilai yang dimasukkan akan disimpan dalam dictionary mahasiswa yang sesuai.
- **Langkah 4**: Setelah berhasil mengubah nilai, program akan menampilkan pesan konfirmasi bahwa data mahasiswa telah berhasil diubah.
- **Langkah 5**: Jika nama yang dimasukkan tidak ditemukan dalam daftar, program akan menampilkan pesan bahwa data mahasiswa tidak ditemukan.

---

## 6. **Fungsi `menu()` - Menampilkan Menu Pilihan Utama**

```python
def menu():
    while True:
        print()
        print("=" * 20)
        print("|   --- MENU ---   |")
        print("=" * 20)
        print("1. Tambah Data")
        print("2. Tampilkan Data")
        print("3. Hapus Data")
        print("4. Ubah Data")
        print("5. Keluar")
        print()
        pilihan = input("Pilih menu (1-5): ")

        if pilihan == "1":
            tambah()
        elif pilihan == "2":
            tampilkan()
        elif pilihan == "3":
            print()
            print("-" * 65)
            nama = input("1. Masukkan nama mahasiswa yang ingin dihapus: ")
            print("-" * 65)
            hapus(nama)
        elif pilihan == "4":
            print()
            print("-" * 55)
            nama = input("1. Masukkan nama mahasiswa yang ingin diubah: ")
            ubah(nama)
        elif pilihan == "5":
            print()
            print("=" * 42)
            print("| --- Program selesai. Terima kasih! --- |")
            print("=" * 42)
            print()
            break
        else:
            print()
            print("=" * 51)
            print("| --- Pilihan tidak valid. Silakan coba lagi! --- |")
            print("=" * 51)
```

- Fungsi ini adalah **menu utama** dari program. Program akan terus-menerus menampilkan menu sampai pengguna memilih untuk keluar dari program.
- Program menampilkan pilihan menu untuk:
  - Menambahkan data (`1`).
  - Menampilkan data (`2`).
  - Menghapus data berdasarkan nama (`3`).
  - Mengubah nilai mahasiswa berdasarkan nama (`4`).
  - Keluar dari program (`5`).
- Program meminta pengguna untuk memilih angka antara 1 sampai 5, dan berdasarkan pilihan tersebut, program akan mengeksekusi fungsi yang sesuai. Jika pilihan tidak valid, program akan menampilkan pesan kesalahan dan meminta pengguna untuk mencoba lagi.
- Program akan berhenti ketika pengguna memilih opsi untuk keluar (pilihan `5`).

---

## 7. **Menjalankan Program**

```python
menu()
```

- Di akhir program, fungsi `menu()` dipanggil untuk memulai seluruh proses.
- Program akan terus berjalan, memungkinkan pengguna untuk berinteraksi dengan menu sesuai pilihan yang diambil.

---
** Hasil

![Screenshot 2024-12-02 222314](https://github.com/user-attachments/assets/66199b17-534d-4b66-9f76-a7eb55b3376d)


![Screenshot 2024-12-02 222332](https://github.com/user-attachments/assets/7bb0c449-a99d-4e46-9007-548a76d8ff4a)

** Flowchat

![WhatsApp Image 2024-12-02 at 17 30 28_3cd27e21](https://github.com/user-attachments/assets/ceb1e859-82a6-4eb8-a911-25577efd1831)

