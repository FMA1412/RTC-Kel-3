# RTC-Kel-3
# Nama Kelompok: Kelompok 3
               1. Fahmi Maulana Ahmad (2042221053)
               2. Yus Putri Arum Segar ( 2042221068 )
               3. Nicholas Marthin Taihuttu ( 2042221002)
# Nama Supervisor: Ahmad Radhy, S.Si., M.Si
# Nama Departemen dan Institut: Departemen Teknik Instrumentasi - Institut Teknologi Sepuluh Nopember

# Tugas Rekayasa Teknologi Cerdas

1. Taylor Series
# 📐 RIZZ - Kalkulasi Sinus dan Kosinus dengan Deret Taylor Berbasis Rust

Proyek ini adalah implementasi fungsi matematika **sinus** dan **kosinus** menggunakan **deret Taylor** dalam bahasa Rust. Perhitungan dilakukan tanpa menggunakan fungsi built-in `f64::sin()` atau `f64::cos()`, tetapi melalui pendekatan numerik deret.


## 🧭 Struktur Proyek

RIZZ/
├── src/
│   └── main.rs           # Program utama: perhitungan sin(x) dan cos(x)
├── Cargo.toml            # Konfigurasi proyek & dependensi (jika ada)
├── Cargo.lock            # Dikunci saat build untuk reproducibility
├── target/               # Folder otomatis dari proses build


## ⚙️ Penjelasan Program

### 🔢 Fungsi Utama

* `factorial(n: u64)`: Menghitung faktorial dari `n`
* `sine(x: f64, terms: u32)`: Menghitung nilai sin(x) dengan deret Taylor sebanyak `terms`
* `cosine(x: f64, terms: u32)`: Menghitung nilai cos(x) dengan deret Taylor sebanyak `terms`

### 🧠 Rumus Taylor

rust
sin(x) ≈ Σ ((-1)^n * x^(2n+1)) / (2n+1)!
cos(x) ≈ Σ ((-1)^n * x^(2n)) / (2n)!


## 💻 Cara Menjalankan di Terminal (VS Code)

1. **Buka VS Code**, arahkan ke folder `RIZZ/`:

   * Klik kanan > **"Open with Code"**

2. **Pastikan Rust Sudah Terinstall**
   Cek versi:

   bash
   rustc --version
   

3. **Build Proyek (Opsional)**:

   bash
   cargo build --release
  

4. **Jalankan Program:**

   bash
   cargo run

5. **Output di Terminal:**

   text
   sin(30) ≈ 0.500000
   cos(30) ≈ 0.866025
  

## 📦 Kelebihan Proyek

✅ Akurasi hasil tergantung jumlah `terms` (default dari program)
✅ Tidak bergantung pada fungsi bawaan math Rust
✅ Bisa dikembangkan untuk fungsi lain (tan, ln, e^x, dsb)


## 📝 Catatan Tambahan

* Nilai input `x` dalam contoh adalah dalam satuan **radian**
* Hasil sudah cukup akurat untuk `terms` ≥ 10
* Proyek ini cocok untuk pembelajaran dasar **numerik dan algoritma deret**

## 🖼️ Hasil
sin(30) ≈ 0.500000
cos(30) ≈ 0.866025


2. Lookup Table
# TUGASRTC - Lookup Table Sinus & Kosinus Berbasis Rust

Proyek ini merupakan program sederhana berbasis Rust untuk menghasilkan **lookup table** nilai sinus dan kosinus dari sudut 0° hingga 90° dengan interval 1 derajat. Lookup table ini disimpan menggunakan fitur `lazy_static` agar dapat digunakan secara efisien dalam berbagai perhitungan.


## 🧭 Struktur Proyek

NO2/
├── src/
│   └── main.rs             # Program utama: generate dan akses tabel sin/cos
├── Cargo.toml              # Metadata proyek dan dependensi (lazy_static)
├── Cargo.lock              # File penguncian versi crate

## ⚙️ Penjelasan Program

* Menggunakan crate `lazy_static` untuk membuat **tabel statis** (LUT: Lookup Table) yang hanya dihitung sekali saat program dijalankan.
* Mengisi dua array: `SIN_LUT` dan `COS_LUT` sebanyak 91 elemen (untuk sudut 0° sampai 90°).
* Nilai dihitung dengan rumus:

 rust
  table[i] = (i as f64 * PI / 180.0).sin(); // untuk SIN_LUT
  table[i] = (i as f64 * PI / 180.0).cos(); // untuk COS_LUT
  
Contoh pengisian:

rust
let mut table = [0.0; LUT_SIZE];
for i in 0..LUT_SIZE {
    table[i] = (i as f64 * PI / 180.0).sin();
}


## 💻 Langkah Menjalankan Proyek

### 1. **Buka Folder di VS Code**

* Klik kanan pada folder `NO2` → **Open with Code**
* Pastikan file `main.rs` dan `Cargo.toml` sudah ada.

### 2. **Build Proyek**

bash
cargo build --release


* Akan menghasilkan file binary di `target/release/no2.exe`

### 3. **Jalankan Program**

bash
cargo run


* Program akan meminta input:

  Masukkan sudut dalam derajat:

* Masukkan sudut antara `0` hingga `90`, lalu enter

### 4. **Contoh Output**

Masukkan sudut dalam derajat: 30
Sin(30°) ≈ 0.5
Cos(30°) ≈ 0.866025

## 📦 Setup & Dependensi

Pastikan Rust sudah terinstal:

bash
rustc --version

**Tambahkan dependency berikut di Cargo.toml**:

toml
[dependencies]
lazy_static = "1.4"


## 📝 Catatan Tambahan

* Lookup table sangat berguna untuk mempercepat komputasi pada sistem embedded atau IoT tanpa floating point unit (FPU).
* Program dapat dikembangkan lebih lanjut untuk:

  * Menyimpan hasil ke file CSV
  * Menyediakan antarmuka Qt untuk input & output visual
  * Menambahkan tan(), cot(), dsb.

## 🖼️ Hasil
Masukkan sudut dalam derajat: 
23
sin(23) ≈ 0.390731
cos(23) ≈ 0.920505

   
3. KNN & SVM
# 📘 Sistem Prediksi Kegagalan Mesin Berbasis Rust

Proyek ini dikembangkan menggunakan bahasa pemrograman **Rust** dengan algoritma klasifikasi seperti **SVM (Support Vector Machine)** dan **kNN (k-Nearest Neighbors)** untuk mendeteksi jenis kerusakan mesin berdasarkan parameter seperti Air temperature [K], Process temperature [K], Rotational speed [rpm], Torque [Nm], Tool wear [min].

## 📂 Struktur Proyek

COBACOBA/
├── csv/                               # Folder berisi dataset CSV
│   └── predictive_maintenance.csv     # Dataset utama
│
├── src/
│   ├── main.rs                        # Entry point utama, handle prediksi & logika
│
├── Cargo.toml                         # File konfigurasi dan dependensi Rust
├── Cargo.lock                         # File lock otomatis dari Cargo


## 🚀 Setup & Instalasi Awal

1. **Pastikan Rust sudah terinstal**

   bash
   rustc --version
   cargo --version

   Jika belum terinstal: [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install)

2. **Clone atau buka folder proyek di VS Code**

   * Bisa dari GitHub atau unzip file proyek lokal.
   * Jalankan Visual Studio Code, buka folder `COBACOBA/`.

3. **Cek dan install dependensi dari `Cargo.toml`**
   Di file ini kamu akan lihat dependensi seperti:

   * `linfa`, `linfa-logistic`: Untuk algoritma ML (SVM).
   * `ndarray`: Untuk manipulasi array/data matrix.
   * `rand`, `csv`, dan lainnya.


## 🧱 Struktur Kode `main.rs`

Berdasarkan gambar, berikut penjelasan isi dari file `main.rs`:

* Import crate eksternal dan standar.
* Fungsi `euclidean_distance`: Menghitung jarak antar vektor (untuk kNN).
* Fungsi `failure_to_label`: Konversi label dari string ke angka (enum manual).

Contoh:

rust
fn failure_to_label(failure: &str) -> usize {
    match failure {
        "No Failure" => 0,
        "Heat Dissipation Failure" => 1,
        "Power Failure" => 2,
        "Random Failures" => 3,
        "Tool Wear Failure" => 4,
        _ => 0,
    }
}


## 🖥️ Cara Menjalankan Program via Terminal

1. Buka terminal di VS Code (CTRL + \`)
2. Pastikan berada di root folder proyek (COBACOBA/)
3. Jalankan dengan perintah:

   bash
   cargo run
   
4. Program akan:

   * Membaca data dari `predictive_maintenance.csv`
   * Melatih model
   * Meminta input manual (jika diminta)
   * Menampilkan hasil prediksi SVM dan kNN seperti ini:

     Prediksi Input Manual:
     SVM: Power Failure
     kNN: Power Failure

## 📌 Tips Debugging

* Jika muncul error `crate not found` → pastikan dependensi ditulis benar di `Cargo.toml`.
* Jika ingin re-run bersih:

  bash
  cargo clean
  cargo build
  cargo run

## 🖼️ Hasil Prediksi

Contoh input:

Air temperature [K]: 300
Process temperature [K]: 310
Rotational speed [rpm]: 1500
Torque [Nm]: 50
Tool wear [min]: 20

Hasil:
Akurasi Model SVM: 97.08%
Akurasi Model KNN: 96.26%

Hasil Prediksi 10 Sampel:
Sampel 1: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 2: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 3: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 4: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 5: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 6: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 7: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 8: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 9: SVM = No Failure, KNN = No Failure, Aktual = No Failure
Sampel 10: SVM = No Failure, KNN = No Failure, Aktual = No Failure

Prediction: No Failure
Probabilities:
- No Failure: 84.97%
- Heat Dissipation Failure: 0.00%
- Power Failure: 0.08%
- Random Failures: 10.27%
- Tool Wear Failure: 4.65%

 

4. NN & qt
# 🚀 Predictive Maintenance - Sistem Klasifikasi Kerusakan Mesin Berbasis Rust Neural Network

Proyek ini adalah sistem klasifikasi jenis kerusakan mesin menggunakan **Neural Network berbasis Rust**. Model dilatih menggunakan dataset *predictive maintenance*, disimpan ke dalam file `.bin`, dan dapat melakukan prediksi interaktif dari terminal. Proyek ini dapat dikembangkan lebih lanjut dengan Qt.



## 🧭 Struktur Proyek


Coba3/
├── csv/                        # Folder dataset (jika ada)
├── plots/                      # Folder untuk grafik loss/akurasi
├── src/
│   └── main.rs                 # Program utama Neural Network
├── trained_model.bin           # Model hasil pelatihan (serialize)
├── training_plot.png           # Grafik loss/akurasi selama training
├── model.bin                   # Versi lain dari model NN
├── qt.py                       # (Opsional) Binding ke Qt 
├── Cargo.toml                  # Konfigurasi dependensi Rust
├── Cargo.lock


## 📦 Langkah Instalasi & Menjalankan Program

### 1. Clone/Download Proyek

Jika dari GitHub:

bash
git clone https://github.com/nama-akun/Coba3.git
cd Coba3


Atau jika dari file ZIP:

* Ekstrak file zip
* Buka folder `Coba3` di VS Code


### 2. Buka dengan VS Code

* Klik kanan folder `Coba3`, lalu **Open with VS Code**
* Pastikan sudah install [Rust Analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer)


### 3. Build dan Jalankan Program

bash
cargo run


Program akan meminta input manual seperti:

text
Air temperature [K]: 300
Process temperature [K]: 310
Rotational speed [rpm]: 1500
Torque [Nm]: 50
Tool wear [min]: 20


Dan akan menghasilkan output klasifikasi:

text
Prediction: No Failure
Probabilities:
No Failure: 84.97%
Heat Dissipation Failure: 0.00%
Power Failure: 0.08%
Random Failures: 10.27%
Tool Wear Failure: 4.65%


## 📦 Dependensi Utama (Cargo.toml)

Proyek ini menggunakan dependensi berikut:

toml
[package]
name = "Coba3"
version = "0.1.0"
edition = "2024"

[lib]
name = "predictive_maintenance"
path = "src/lib.rs"
crate-type = ["cdylib"]


[dependencies]
ndarray = { version = "0.15", features = ["serde"] }
ndarray-rand = "0.14"
rand = "0.8"
csv = "1.1"
libc = "0.2"
plotters = "0.3"
serde = { version = "1.0", features = ["derive"] }
bincode = "1.3"
indicatif = "0.17"


## 🧱 Struktur Kode

### Struktur Data

rust
#[derive(Serialize, Deserialize)]
struct TrainedModel {
    network: NeuralNetwork,
    x_mean: Array1<f64>,
    x_std: Array1<f64>,
    class_weights: Vec<f64>,
}

#[derive(Serialize, Deserialize)]
struct TrainingHistory {
    epochs: Vec<usize>,
    accuracies: Vec<f64>,
    losses: Vec<f64>,
}


### Fitur Program

✅ Normalisasi input dengan mean dan std dari pelatihan
✅ Neural network multilayer
✅ Probabilitas hasil klasifikasi
✅ Simpan dan muat model `.bin`
✅ Plot training (loss dan akurasi)
✅ Input manual dari user


## 🖼️ Hasil Prediksi

Contoh input:


Air temperature [K]: 300
Process temperature [K]: 310
Rotational speed [rpm]: 1500
Torque [Nm]: 50
Tool wear [min]: 20


Hasil:

🔧 Starting Predictive Maintenance System
🎓 Training new model...
Class distribution: [626, 112, 92, 15, 44]
Class weights: [0.2840255591054313, 1.5875, 1.932608695652174, 11.853333333333333, 4.040909090909091]
Epoch 0 - Loss: 1.4813 - Test Accuracy: 52.25%
Epoch 100 - Loss: 0.5009 - Test Accuracy: 87.64%
Epoch 200 - Loss: 0.4588 - Test Accuracy: 89.89%
Epoch 300 - Loss: 0.4569 - Test Accuracy: 89.33%
Epoch 400 - Loss: 0.4609 - Test Accuracy: 88.76%
Epoch 500 - Loss: 0.4667 - Test Accuracy: 88.76%
Epoch 600 - Loss: 0.4720 - Test Accuracy: 88.76%
Epoch 700 - Loss: 0.4782 - Test Accuracy: 88.76%
Epoch 800 - Loss: 0.4850 - Test Accuracy: 88.76%
Epoch 900 - Loss: 0.4923 - Test Accuracy: 88.76%
Epoch 1000 - Loss: 0.4978 - Test Accuracy: 89.33%
Epoch 1100 - Loss: 0.5037 - Test Accuracy: 89.33%
Epoch 1200 - Loss: 0.5078 - Test Accuracy: 89.33%
Epoch 1300 - Loss: 0.5122 - Test Accuracy: 89.33%
Epoch 1400 - Loss: 0.5152 - Test Accuracy: 89.33%
Epoch 1500 - Loss: 0.5185 - Test Accuracy: 89.89%
Epoch 1600 - Loss: 0.5216 - Test Accuracy: 89.89%
Epoch 1700 - Loss: 0.5241 - Test Accuracy: 89.89%
Epoch 1800 - Loss: 0.5266 - Test Accuracy: 89.89%
Epoch 1900 - Loss: 0.5285 - Test Accuracy: 89.89%
✅ Final Test Accuracy: 90.45%
Sample predictions vs true labels:
Pred: 2 vs True: 2
Pred: 0 vs True: 0
Pred: 0 vs True: 0
Pred: 0 vs True: 0
Pred: 0 vs True: 1

🔮 Enter machine parameters (or 'q' to quit):
🔍 Prediction: Tool Wear Failure
📊 Probabilities:
  No Failure: 22.13%
  Heat Dissipation Failure: 0.00%
  Power Failure: 0.00%
  Random Failures: 0.07%
  Tool Wear Failure: 77.79%

 
