# Laporan Proyek UAS Penggalian Data dan Perolehan Informasi - Dior Herdian dan Basuki R Zamzami

## Project Overview

**Latar Belakang Proyek**

Air merupakan salah satu kebutuhan dasar manusia yang sangat penting untuk mendukung berbagai aspek kehidupan, seperti kebutuhan rumah tangga, industri, pertanian, hingga kesehatan. Dalam konteks perkotaan seperti DKI Jakarta, ketersediaan air bersih menjadi tantangan yang semakin kompleks karena pertumbuhan penduduk, urbanisasi, serta peningkatan aktivitas ekonomi. Sebagai salah satu sumber air yang banyak digunakan oleh masyarakat, air sumur sering kali menjadi pilihan utama, terutama di wilayah yang belum sepenuhnya terlayani oleh jaringan air perpipaan.

Namun, kualitas air sumur di DKI Jakarta semakin menjadi perhatian karena potensi pencemaran akibat berbagai aktivitas manusia, seperti pembuangan limbah domestik, industri, dan aktivitas lainnya. Sebagai kota metropolitan dengan tingkat kepadatan penduduk yang tinggi, risiko pencemaran air tanah di DKI Jakarta juga meningkat seiring dengan penurunan kualitas lingkungan. Oleh karena itu, penting untuk melakukan pemantauan secara berkala terhadap kualitas air sumur guna memastikan bahwa air tersebut masih layak untuk digunakan.

Dinas Lingkungan Hidup Provinsi DKI Jakarta secara rutin melakukan pemantauan kualitas air sumur di berbagai lokasi untuk mengidentifikasi tingkat pencemaran dan memastikan bahwa kualitas air tersebut sesuai dengan baku mutu yang telah ditetapkan. Pemantauan ini melibatkan pengujian parameter-parameter fisik, kimia, dan biologi, seperti pH, kekeruhan, kandungan logam berat, dan keberadaan mikroorganisme patogen.

Pada tahun 2022, Dinas Lingkungan Hidup telah melaksanakan pemantauan kualitas air sumur di seluruh wilayah DKI Jakarta. Data yang diperoleh dari pemantauan ini sangat penting untuk diolah dan dianalisis guna mendapatkan gambaran menyeluruh mengenai kondisi kualitas air sumur di wilayah tersebut.

Melalui pengolahan dan analisis data yang akurat, diharapkan hasil dari pemantauan ini dapat memberikan kontribusi yang signifikan dalam upaya peningkatan kualitas lingkungan, khususnya kualitas air tanah di Provinsi DKI Jakarta. Selain itu, hasil analisis juga dapat digunakan untuk meningkatkan kesadaran masyarakat mengenai pentingnya menjaga kebersihan lingkungan demi keberlanjutan sumber daya air yang sehat dan aman.

**Pentingnya Proyek**

Proyek ini penting karena:

1. Dapat membantu dalam menentukan tingkat kesesuaian kualitas air sumur terhadap baku mutu air bersih yang ditetapkan oleh pemerintah.
2. Mempercepat identifikasi wilayah-wilayah yang memiliki tingkat pencemaran tinggi sehingga memerlukan tindakan pengendalian atau mitigasi lebih lanjut.
3. Dapat memberikan informasi yang dapat menjadi dasar dalam pengambilan kebijakan terkait pengelolaan sumber daya air di DKI Jakarta.

## Business Understanding

### Problem Statements

- Bagaimana kita dapat mempercepat proses clustering untuk mengelompokkan kualitas air sumur berdasarkan hasil pemantauan yang sudah dilakukan oleh Pemerintah
- Bagaimana kita dapat mengklasifikasikan kualitas sumur air sesuai standar sehingga dapat memberikan tindakan mitigasi lebih lanjut

### Goals

- Mengembangkan model klasifikasi dan regresi untuk mengelompokan hasil kualitas air sumur sehingga dapat memberikan informasi untuk pengambilan keputusan.
- Membuat sistem analisis yang dapat memberikan informasi terkait klasifikasi kualitas sumur air serta mitigasi atau proses penanganan lebih lanjut.

### Solution statements

- Model Klasifikasi : Menggunakan model klasifikasi dari data hasil pengambilan kualitas air sumur seperti kadar besi untuk diklasifikasikan kedalam kategori "Di Atas Standar" atau "Dalam Standar".
- Model Regresi : Menggunakan model regresi dari data hasil pengambilan kualitas air sumur seperti kadar besi untuk dibandingkan dengan baku mutu kualitas air sumur yang sudah ditetapkan.
  
## Data Understanding

Data Kualitas Air Sumur di Provinsi DKI Jakarta berdasarkan hasil pemantauan yang dilakukan oleh Dinas Lingkungan Hidup per periode pemantauan tahun 2022. Dataset ini dapat diperoleh dari link berikut : https://satudata.jakarta.go.id/open-data/detail/data-kualitas-air-sumur-2022

 #   Column           Non-Null Count  Dtype 
---  ------           --------------  ----- 
 0   periode_data     11814 non-null  int64 
 1   tahun            11814 non-null  int64 
 2   periode          11814 non-null  int64 
 3   waktu_sampling   11814 non-null  object
 4   nama_lokasi      11814 non-null  object
 5   kecamatan        11814 non-null  object
 6   lintang_selatan  11814 non-null  object
 7   bujur_timur      11814 non-null  object
 8   parameter        11814 non-null  object
 9   satuan           11814 non-null  object
 10  baku_mutu        11814 non-null  object
 11  nilai            11814 non-null  object

Variabel-variabel pada dataset adalah sebagai berikut:
- `periode_data` : Penjelasan Periode Data 1 Tahun
- `tahun` : adalah tahun dilakukannya pemantauan
- `periode` : adalah periode pelaksanaan pemantauan
- `waktu_sampling` : adalah waktu pengambilan sampel air untuk keperluan pemantauan
- `nama_lokasi` : adalah nama lokasi pengambilan sampel
- `kecamatan` : adalah nama kecamatan tempat pengambilan sampel dilakukan
- `lintang_selatan` : adalah koordinat lintang selatan lokasi pengambilan sampel
- `bujur_timur` : adalah koordinat bujur timur lokasi pengambilan sampel
- `parameter` : adalah nama parameter yang dipantau
- `satuan` : adalah satuan ukur parameter
- `baku_mutu` : adalah nilai ambang batas yang diizinkan menurut ketentuan yang berlaku
- `nilai` : adalah hasil pengukuran parameter yang dipantau

## Data Preparation

**Teknik Data Preparation**

- Load data dari dataset yang dipilih (kualitas air sumur)
- Menampilkan informasi (kolom dan jenis data) dari dataset yang dipilih
- Menampilkan informasi head data dari masing-masing kolom dataset

**Proses Data Preparation**

- Membuat salinan data parameter menjadi Besi Fe
- Konversi kolom 'nilai' dan 'baku_mutu' menjadi numerik, mengganti koma dengan titik

**Alasan Tahapan Data Preparation**

- Data parameter kita salin menjadi Besi Fe untuk menjaga keaslian dari data asli yang ada di dataset, adapun konversi kolom 'nilai' dan 'baku_mutu' menjadi numerik untuk memudahkan dalam modeling yang dilakukan.

## Modeling

**Klasifikasi**

Pada tahap ini akan membahas pendekatan Klasifikasi. Berikut adalah penjelasan lebih lanjut mengenai parameter yang digunakan dari pendekatan tersebut.

Tahapan Proses Klasifikasi :

1. **Menggunakan Klasifikasi**

    ```python
   conf_matrix = confusion_matrix(y_test, y_pred)
    sns.heatmap(conf_matrix, annot=True, fmt='d', cmap='Blues', xticklabels=label_encoders['status'].classes_, yticklabels=label_encoders['status'].classes_)
    plt.xlabel("Prediksi")
    plt.ylabel("Aktual")
    plt.title("Confusion Matrix")
    plt.show()
    ```

    Hasilnya akan sebagai berikut
    ![MetodeKlasifikasi](https://github.com/basukizamzami/kualitas-sumur-air/blob/main/images/MetodeKlasifikasi.png)

   Pendekatan klasifikasi digunakan karena tujuan utama adalah untuk mengelompokkan data menjadi dua kategori: 'Di Atas Standar' dan 'Dalam Standar'. Metode ini cocok ketika variabel target bersifat kategoris dan tidak memerlukan prediksi nilai numerik yang spesifik.

3. **Menggunakan Regresi**

    ```python
    plt.figure(figsize=(10, 6))
    plt.scatter(data_besi['baku_mutu'], data_besi['nilai'], c=data_besi['status'], cmap='coolwarm', alpha=0.7)
    plt.colorbar(label='Status (Encoded)')
    plt.xlabel("Baku Mutu")
    plt.ylabel("Nilai")
    plt.title("Scatter Plot: Nilai vs Baku Mutu")
    plt.show()

    print("Scatter Plot memvisualisasikan hubungan antara 'nilai' dan 'baku_mutu'.")
    print("Titik di atas garis y=x (di mana nilai > baku_mutu) dikategorikan sebagai 'Di Atas Standar',")
    print("sedangkan titik di bawah dikategorikan sebagai 'Dalam Standar'.")
    ```

   Hasilnya akan sebagai berikut
    ![MetodeRegresi](https://github.com/basukizamzami/kualitas-sumur-air/blob/main/images/MetodeRegresi.png)

   Pendekatan regresi dapat digunakan jika tujuan adalah untuk memprediksi nilai numerik ('nilai') secara spesifik. Setelah prediksi nilai, dapat dibandingkan dengan 'baku_mutu' untuk menentukan apakah berada di atas atau dalam standar." Namun, regresi memerlukan langkah tambahan dan biasanya lebih kompleks jika fokus utama hanya pada klasifikasi kategori.
