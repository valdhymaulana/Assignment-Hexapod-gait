# Hexapod Tripod Gait Assignment

## Deskripsi Tugas
Tugas ini adalah merancang dan mengimplementasikan scheduler gerak untuk robot hexapod menggunakan *tripod gait*. Pada pola ini, setiap langkah menjaga tiga kaki berada di tanah secara bersamaan sehingga membentuk segitiga penyangga yang stabil.

## Tujuan
- Memodifikasi scheduler gait awal agar dapat menangani 6 kaki: `L1`, `L2`, `L3`, `R1`, `R2`, `R3`
- Menentukan matriks `offsets` untuk pola *tripod gait*
- Menentukan nilai `duty factor` yang sesuai agar gait tetap stabil
- Memvisualisasikan diagram gait untuk semua kaki
- Memverifikasi stabilitas dengan memastikan minimal 3 kaki berada di *stance* setiap saat
- Menyajikan analisis perbedaan stabilitas antara *Trot Quadruped* dan *Tripod Hexapod*

## Implementasi
- Dibuat kelas `HexapodTripodGaitScheduler` yang memperluas scheduler quadruped sebelumnya
- Menggunakan `hexapod_legs = ['L1', 'L2', 'L3', 'R1', 'R2', 'R3']`
- Offset tripod dipilih sebagai:
  - `hexapod_offsets = [0.0, 0.5, 0.0, 0.5, 0.0, 0.5]`
- `duty factor` diatur sekitar `0.60` untuk menjaga fase *stance* lebih panjang dan memberikan margin stabilitas
- Diagram gait menampilkan fase *stance* berwarna biru dan *swing* berwarna abu-abu
- Verifikasi dilakukan dengan menghitung jumlah kaki di *stance* sepanjang satu siklus

## Hasil
- Pola *tripod gait* berhasil divisualisasikan untuk 6 kaki
- Verifikasi menunjukkan selalu ada setidaknya 3 kaki di tanah pada setiap titik waktu
- Gait ini lebih stabil secara statis karena selalu mempertahankan segitiga kontak

## Analisis Stabilitas
- **Trot Quadruped**:
  - Hanya dua kaki diagonal yang berada di *stance* secara bersamaan
  - Area dukungan lebih kecil, sehingga bergantung pada kontrol dinamis dan momentum
- **Tripod Hexapod**:
  - Selalu mempertahankan tiga kaki di *stance*
  - Membentuk segitiga penyangga yang lebih besar dan lebih tahan terhadap gangguan
- Akibatnya, tripod gait hexapod lebih stabil secara statis dibanding trot pada quadruped
