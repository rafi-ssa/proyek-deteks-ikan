# README - Integrasi Model YOLOv8 ke Aplikasi Streamlit

## Deskripsi Project

Project ini merupakan aplikasi **Deteksi dan Klasifikasi Jenis Ikan** menggunakan **YOLOv8** sebagai model Artificial Intelligence dan **Streamlit** sebagai antarmuka (web localhost).

Pembagian tugas:

* **Bagian AI (Saya)**

  * Mengumpulkan dan menggabungkan dataset.
  * Melakukan anotasi menggunakan Roboflow.
  * Melatih (training) model YOLOv8.
  * Menghasilkan file model `best.pt`.
  * Menyerahkan model kepada bagian frontend.

* **Bagian Frontend (Teman)**

  * Membuat tampilan aplikasi menggunakan Streamlit.
  * Menghubungkan Streamlit dengan model `best.pt`.
  * Menampilkan hasil deteksi kepada pengguna.

---

# Struktur Project

```
fish_detection_streamlit/
│
├── app.py
├── requirements.txt
├── README.md
│
├── model/
│   └── best.pt
│
├── pages/
│   ├── 1_Home.py
│   ├── 2_Deteksi.py
│   ├── 3_Dataset.py
│   ├── 4_Hasil_Training.py
│   └── 5_Tentang.py
│
├── utils/
│   ├── detector.py
│   ├── image_utils.py
│   └── helper.py
│
├── assets/
│   ├── logo.png
│   ├── banner.png
│   └── ikan.png
│
├── uploads/
├── results/
│
└── dataset/
```

---

# Cara Kerja Sistem

```
Dataset
      │
      ▼
Training YOLOv8
      │
      ▼
best.pt
      │
      ▼
Streamlit
      │
Upload Gambar
      │
      ▼
Model Melakukan Prediksi
      │
      ▼
Menampilkan Hasil Deteksi
```

---

# Model

Model yang digunakan:

* YOLOv8
* File model:

  ```
  model/best.pt
  ```

Frontend **tidak perlu melakukan training ulang**.

Frontend hanya perlu memanggil model tersebut untuk melakukan prediksi.

---

# Halaman yang Dibuat

## 1. Home

Berisi:

* Judul aplikasi
* Penjelasan singkat
* Tombol menuju halaman deteksi
* Banner atau gambar

---

## 2. Deteksi Ikan

Fitur utama aplikasi.

Harus memiliki:

* Upload gambar
* Preview gambar
* Tombol Deteksi
* Menampilkan:

  * Gambar hasil deteksi
  * Nama jenis ikan
  * Confidence (%)

Opsional:

* Download hasil deteksi

---

## 3. Dataset

Menampilkan informasi dataset.

Contoh:

* Jumlah kelas ikan
* Nama setiap kelas
* Contoh gambar tiap kelas

---

## 4. Hasil Training

Menampilkan performa model.

Misalnya:

* Accuracy
* Precision
* Recall
* mAP
* Confusion Matrix
* Grafik hasil training

Data ini berasal dari hasil training YOLO.

---

## 5. Tentang

Berisi:

* Judul Project
* Metode
* Teknologi yang digunakan

Contoh:

* Python
* Streamlit
* YOLOv8
* Roboflow
* OpenCV

---

# Integrasi Model

Model berada pada folder:

```
model/
    best.pt
```

Contoh pemanggilan model:

```python
from ultralytics import YOLO

model = YOLO("model/best.pt")
```

Ketika user mengupload gambar:

```
User Upload
      │
      ▼
best.pt
      │
      ▼
Prediksi
      │
      ▼
Menampilkan Bounding Box
```

---

# Output yang Diharapkan

Setelah pengguna mengupload gambar, aplikasi menampilkan:

* Gambar hasil deteksi
* Bounding Box
* Nama ikan
* Confidence
* Jumlah objek yang terdeteksi (jika lebih dari satu)

---

# Catatan

* Jangan mengubah file `best.pt`.
* Folder `model/` hanya digunakan untuk menyimpan model hasil training.
* Jika model diperbarui, cukup mengganti file `best.pt` tanpa perlu mengubah tampilan aplikasi.
* Seluruh proses training dilakukan pada notebook (`.ipynb`). Streamlit hanya berfungsi sebagai antarmuka pengguna untuk menjalankan prediksi menggunakan model yang sudah dilatih.

---

# Tujuan Akhir

Membuat aplikasi berbasis web menggunakan Streamlit yang memungkinkan pengguna:

1. Mengunggah gambar ikan.
2. Model YOLOv8 melakukan deteksi dan klasifikasi secara otomatis.
3. Hasil deteksi ditampilkan secara informatif dengan antarmuka yang mudah digunakan.
