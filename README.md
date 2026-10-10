# Klasifikasi Angka Tulisan Tangan (MNIST) menggunakan TensorFlow

Proyek ini adalah implementasi *Deep Learning* tingkat pemula hingga menengah menggunakan **TensorFlow** dan **Keras** untuk mengklasifikasikan gambar angka tulisan tangan (0 sampai 9) menggunakan dataset standar **MNIST**. Proyek ini dirancang dan dijalankan di lingkungan **Google Colab**.

---

## 📋 Daftar Isi
- [Tentang Proyek](#-tentang-proyek)
- [Arsitektur Model](#-arsitektur-model)
- [Tahapan Proyek](#-tahapan-proyek)
- [Hasil Pelatihan & Evaluasi](#-hasil-pelatihan--evaluasi)
- [Cara Menjalankan di Google Colab](#-cara-menjalankan-di-google-colab)
- [Persyaratan Sistem](#-persyaratan-sistem)

---

## 🎯 Tentang Proyek
Tujuan dari proyek ini adalah melatih model Jaringan Saraf Tiruan (*Artificial Neural Network* / ANN) agar dapat mengenali dan mengklasifikasikan gambar digit angka tulisan tangan dengan akurasi tinggi. Dataset yang digunakan adalah **MNIST**, yang berisi:
- **60.000 gambar** data pelatihan (*training data*).
- **10.000 gambar** data pengujian (*testing data*).
- Setiap gambar berukuran **28x28 piksel** dalam skala keabuan (*grayscale*).

---

## 🏗️ Arsitektur Model
Model yang digunakan adalah model sekuensial (*Sequential Model*) dengan lapisan-lapisan berikut:
1. **Flatten Layer**: Mengubah bentuk gambar matriks 2D (ukuran $28 \times 28$ piksel) menjadi vektor 1D dengan 784 nilai.
2. **Dense (Hidden) Layer**: Lapisan tersembunyi dengan **128 neuron** dan fungsi aktivasi **ReLU** (*Rectified Linear Unit*) untuk mempelajari pola kompleks dari piksel gambar.
3. **Dropout Layer (0.2)**: Mengabaikan 20% neuron secara acak selama pelatihan guna mencegah *overfitting* (model menghafal data alih-alih belajar).
4. **Dense (Output) Layer**: Lapisan akhir dengan **10 neuron** (mewakili angka 0 hingga 9) menggunakan fungsi aktivasi **Softmax** untuk menghasilkan probabilitas dari masing-masing kelas angka.

---

## ⚙️ Tahapan Proyek
Berdasarkan *notebook* yang dibuat, berikut adalah alur kerja program:

1. **Pemeriksaan Versi TensorFlow**: 
   Memastikan versi TensorFlow yang digunakan (tercatat versi `2.21.0`).
2. **Memuat Dataset**: 
   Mengambil dataset MNIST langsung dari modul bawaan `tf.keras.datasets.mnist`.
3. **Pra-pemrosesan Data (Normalisasi)**: 
   Membagi nilai piksel dengan `255.0` agar rentang warna berubah dari `[0, 255]` menjadi `[0.0, 1.0]`, yang membantu model belajar lebih stabil dan cepat konvergen.
4. **Kompilasi Model**:
   - **Optimizer**: `adam` (efisien untuk penyesuaian bobot jaringan).
   - **Loss Function**: `sparse_categorical_crossentropy` (karena label berupa integer dari 0-9).
   - **Metrics**: `accuracy` (untuk mengukur tingkat keberhasilan tebakan model).
5. **Pelatihan Model (`model.fit`)**:
   Model dilatih menggunakan seluruh data latih sebanyak **6 epochs** (putaran penuh).

---

## 📊 Hasil Pelatihan & Evaluasi

Proyek ini telah dijalankan selama **6 epochs** dengan catatan performa per epoch sebagai berikut:

- **Epoch 1/6**: Akurasi: `91.41%` | Loss: `0.2957`
- **Epoch 2/6**: Akurasi: `95.63%` | Loss: `0.1449`
- **Epoch 3/6**: Akurasi: `96.75%` | Loss: `0.1075`
- **Epoch 4/6**: Akurasi: `97.24%` | Loss: `0.0891`
- **Epoch 5/6**: Akurasi: `97.66%` | Loss: `0.0747`
- **Epoch 6/6**: Akurasi: `97.96%` | Loss: `0.0641`

### Hasil Evaluasi pada Data Uji (*Testing Data*):
Saat diuji menggunakan data uji baru yang belum pernah dilihat sebelumnya, model mencetak hasil:
- **Loss**: `0.0688`
- **Akurasi Akhir**: **`97.97%`**

---

## 🚀 Cara Menjalankan di Google Colab
1. Buka [Google Colab](https://colab.research.google.com/).
2. Buat *notebook* baru atau unggah berkas `.ipynb` proyek ini.
3. Pastikan Anda mengaktifkan akselerator perangkat keras (disarankan GPU) melalui menu: 
   `Runtime > Change runtime type > Hardware accelerator (Pilih T4 GPU atau sejenisnya)`.
4. Jalankan sel kode satu per satu dari atas ke bawah.

---

## 🛠️ Persyaratan Sistem
- Python 3.x
- TensorFlow 2.x (`pip install tensorflow`)
