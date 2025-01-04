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
   data_besi['status'] = np.where(data_besi['nilai'] > data_besi['baku_mutu'], 'Di Atas Standar', 'Dalam Standar')
    ```

    Hasilnya akan sebagai berikut
    ![Elbow Method](https://github.com/jakabaskara/clustering-kualitas-minyak-pada-inti-sawit/blob/main/image/ElbowMethod.png)

    Dari gambar tersebut bisa diambil nilai K yang paling optimal adalah 2

    Namun dalam case ini kami mencoba menggunakan 3 cluster karena mendekati standarisasi pembagian yang ada di lapangan yaitu kualitas buruk, kualitas bagus, dan kualitas masih bisa ditingkatkan.

2. **Menggunakan nilai K yang telah ditentukan untuk melakukan K-Means Clustering**

    Pada tahap menuggnakan K-Means Clustering dengan nilai K yang diambil dari perbantuan Elbow Method diatas dilakukan dua kali percobaan yaitu menggunakan nilai K = 2 dan K =3

    Untuk Penggunakan nilai K = 2 pada K-Menas Clustering

    ```python
    optimal_k = 2
    kmeans = KMeans(n_clusters=optimal_k, random_state=42)
    data_inliers['Cluster'] = kmeans.fit_predict(data_pca)

    #Visualisasi Cluster
    plt.figure(figsize=(10, 6))
    for cluster in range(optimal_k):
        plt.scatter(data_pca[data_inliers['Cluster'] == cluster, 0],
                    data_pca[data_inliers['Cluster'] == cluster, 1],
                    label=f'Cluster {cluster}', alpha=0.7, s=100)
    plt.xlabel('Principal Component 1')
    plt.ylabel('Principal Component 2')
    plt.title('Visualisasi Clustering setelah Penanganan Outliers, PCA, dan Normalisasi')
    plt.legend()
    plt.grid(True)
    plt.tight_layout()
    plt.show()
    ```

    Hasilnya seperti berikut :
    ![KMeansClusterKeq2](https://github.com/jakabaskara/clustering-kualitas-minyak-pada-inti-sawit/blob/main/image/KMeansClusterKeq2.png)

    Untuk Penggunakan nilai K = 3 pada K-Means Clustering

    ```python
    optimal_k = 3
    kmeans = KMeans(n_clusters=optimal_k, random_state=42)
    data_inliers['Cluster'] = kmeans.fit_predict(data_pca)

    #Visualisasi Cluster
    plt.figure(figsize=(10, 6))
    for cluster in range(optimal_k):
        plt.scatter(data_pca[data_inliers['Cluster'] == cluster, 0],
                    data_pca[data_inliers['Cluster'] == cluster, 1],
                    label=f'Cluster {cluster}', alpha=0.7, s=100)
    plt.xlabel('Principal Component 1')
    plt.ylabel('Principal Component 2')
    plt.title('Visualisasi Clustering setelah Penanganan Outliers, PCA, dan Normalisasi')
    plt.legend()
    plt.grid(True)
    plt.tight_layout()
    plt.show()
    ```

    Hasilnya seperti berikut :
    ![KMeansClusterKeq3](https://github.com/jakabaskara/clustering-kualitas-minyak-pada-inti-sawit/blob/main/image/KMeansClusterKeq3.png)

    Dan dapat dilihat walaupun secara elbow method memberikan visualisasi jika k = 2 adalah nilai optimal, namun itu tidak menutup kemungkinan untuk k=3 karena secara visual datanya tercluster dengan baik.

## Evaluation

**Silhouette Score:**
Berdasarkan hasil pengujian Silhouette Score berada di angka **0.32** yang berarti Clustering Cukup atau tidak buruk  tetapi juga menunjukkan bahwa clustering Anda memiliki ruang untuk perbaikan.

**Davies-Bouldin Index:** Score Menunjukan di angka **1.06** menunjukkan clustering cukup baik, dengan cluster yang rapat secara internal dan cukup terpisah dari cluster lainnya.

## Kesimpulan

1. **Identifikasi Cluster Lebih Awal pada Inti Sawit.**
Proses clustering yang diterapkan pada data inti sawit dari mesin Foss NIRS memungkinkan identifikasi kategori kualitas minyak lebih awal, bahkan sebelum proses ekstraksi minyak selesai. Hal ini memberikan manfaat besar dibandingkan metode konvensional yang hanya mengandalkan ALB (Asam Lemak Bebas) di tahap akhir proses.
2. **Pengelompokan Berdasarkan Karakteristik Kualitas.** Clustering berhasil mengelompokkan inti sawit ke dalam tiga kategori, yaitu:

   - **Kualitas Buruk:** Inti sawit dengan kandungan minyak rendah atau kualitas tidak memenuhi standar.
   - **Kualitas Masih Dapat Ditingkatkan:** Inti sawit dengan kualitas sedang yang masih memiliki potensi untuk diperbaiki.
   - **Kualitas Baik:** Inti sawit dengan kandungan minyak tinggi dan kualitas yang memenuhi standar.

    Hal ini memberikan informasi yang lebih kaya dibandingkan hanya mempertimbangkan ALB sebagai satu-satunya indikator kualitas.

## Referensi

[1] [FOSS NIRS SAWIT](https://news.kharisma-sawit.com/berita-terkini-beginilah-cara-kerja-foss-nir-pabrik-sawit-efektif-untuk-pks-284#:~:text=Bisa%20dikatakan%20bahwa%20FOSS%20NIRS)
