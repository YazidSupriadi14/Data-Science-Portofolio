# Klasifikasi Gambar: Corn Leaf Diseases

## Deskripsi Proyek
Proyek ini membangun model Convolutional Neural Network (CNN) untuk
mengklasifikasikan gambar daun jagung berdasarkan jenis penyakitnya
(termasuk kategori sehat/healthy). Dataset asli berformat YOLO untuk
object detection, dikonversi menjadi struktur folder per kelas untuk
keperluan klasifikasi gambar.

## Dataset
- Sumber: [CORN Leaf Diseases - Kaggle](https://www.kaggle.com/datasets/yusufmurtaza01/corn-leaf-diseases)
- Jumlah kelas: 4
- Daftar kelas:
- Corn__CommonRust
- Corn__GrayLeafSpot
- Corn__Healthy
- Corn__NorthernLeafBlight
- Dataset dibagi menjadi train (70%), validation (15%), dan test (15%)
- Augmentasi offline (rotasi, flip, brightness, shear, warp shift)
  diterapkan pada data train untuk memperbanyak jumlah gambar
- Augmentasi on-the-fly tambahan diterapkan saat training melalui
  ImageDataGenerator

## Arsitektur Model
Model dibangun menggunakan Keras Sequential API dengan kombinasi
layer Conv2D dan MaxPooling2D, dilanjutkan dengan Flatten, Dropout,
dan Dense layer untuk klasifikasi multi-kelas (aktivasi softmax).

## Callback
- Custom callback `StopAtAccuracy` untuk menghentikan training otomatis
  saat target akurasi tercapai
- EarlyStopping untuk mencegah overfitting

## Format Model yang Disimpan
- `saved_model/` - format TensorFlow SavedModel standar untuk deployment
  server/cloud
- `tflite/model.tflite` - format teroptimasi untuk mobile/embedded,
  disertai `label.txt` berisi nama kelas
- `tfjs_model/` - format TensorFlow.js untuk dijalankan di browser

