# Laporan Proyek Machine Learning - I Putu Bayu Adhya Wiratama

## Domain Projek
---
Dewasa ini, teknologi tidak dapat lepas dari kehidupan manusia. Penggunaan teknologi dapat membantu kehidupan manusia menjadi lebih mudah, seperti dalam hal komunikasi, efisiensi produksi, dan lain-lain. Salah satu bentuk teknologi yang sangat membantu manusia saat ini adalah *Handphone* atau telepon genggam.

Hampir setiap orang di dunia ini memiliki *Handphone* yang digunakan untuk berbagai keperluan, seperti komunikasi jarak jauh, mencari informasi, hingga hiburan. Sudah banyak jenis *handphone* yang beredar di masyarakat dengan spesifikasinya masing-masing. Perbedaan spesifikasi ini membuat harga tiap *handphone* memiliki perbedaan. Perbedaan harga ini kemudian menimbulkan berbagai permasalahan, baik dari sisi penjualan bagi distributor *handphone*, maupun dari sisi *customer* yang ingin membeli *handphone*.

Projek ini bertujuan untuk melakukan klasifikasi kategori harga *handphone* berdasarkan berbagai fitur atau spesifikasi yang dimilikinya. Projek ini mengangkat topik **Telekomunikasi** dengan subbidang **klasifikasi**.

Riset terkait dapat dilihat pada [link berikut](https://www.researchgate.net/publication/333461879_Factors_affecting_mobile_phone_selection).
## Business Understanding
---
Berdasarkan latar belakang permasalahan di atas, beberapa permasalahan yang ingin dipecahkan adalah sebagai berikut.
#### Problem Statement
- Apa saja faktor yang mempengaruhi harga sebuah *handphone*?
- Apakah pendekatan *Machine Learning* dapat digunakan untuk memecahkan permasalahan di atas?
- Model apa yang menghasilkan performa terbaik dalam memecahkan permasalahan di atas?

Berdasarkan *problem statement* di atas, *goals* yang ingin dicapai adalah sebagai berikut.
#### Goals
- Mengetahui faktor yang mempengaruhi harga sebuah *handphone*.
- Mengetahui apakah pendekatan *Machine Learning* dapat digunakan untuk memecahkan permasalahan di atas.
- Mengetahui model apa yang menghasilkan performa terbaik dalam memecahkan permasalahan di atas.

Berdasarkan *goals* yang ingin dicapai, penulis memiliki beberapa solusi yang dapat ditawarkan, diantaranya:
#### Solution Statements
- Melakukan pengujian menggunakan beberapa model *machine learning* sebagai perbandingan.
- Melakukan evaluasi performa masing-masing model untuk mendapatkan perbandingan.

Metriks yang akan digunakan dalam tahap evaluasi untuk kasus klasifikasi antara lain **accuracy**, **precision**, **recall**, dan **f1-score**.
## Data Understanding
---
Dataset yang digunakan dalam projek ini adalah [Mobile Price Dataset](https://www.kaggle.com/datasets/sobhanmohammadids/mobile-price-dataset). Dataset tersebut terdiri dari 2000 sampel dan 21 variabel (20 variabel independen dan 1 variabel dependen). Berikut merupakan penjelasan masing-masing variabel.
#### Variabel
- battery_power	: Kapasitas batre (mAh)
- blue		: Memiliki bluetooth atau tidak
- clock_speed	: kecepatan microprocessor
- dual_sim	: support dual sim atau tidak
- fc		: megapixel kamera depan
- four_g	: mendukung 4G atau tidak
- int_memory : kapasitas memori internal
- m_dep		: ketebalan handphone (cm)
- mobile_wt	: berat hp
- n_cores	: jumlah core processor
- pc		: megapixel kamera belakang (utama)
- px_height	: resolusi tinggi layar (pixel)
- px_width	: resolusi lebar layar (pixel)
- ram		: ukuran RAM
- sc_h		: tinggi layar (cm)
- sc_w		: lebar layar (cm)
- talk_time	: daya tahan baterai saat menelfon
- three_g	: mendukung 3G atau tidak
- touch_screen	: touch screen atau tidak
- wifi		: mendukung wifi atau tidak
- [target] price_range	: range harga (0: low, 1: medium, 2: high, 3: very high)

#### Metode
Metode *data understanding* yang digunakan untuk memahami data adalah ***Exploratory Data Analysis*** (EDA). Beberapa teknik EDA yang dilakukan antara lain:
- *Descriptive Statistics* dengan melihat rata-rata (*mean*), kuartil, nilai minimum dan maximum, serta standar deviasi.
- Melihat persebaran dari masing-masing variabel terhadap label.
- Melihat korelasi antara variabel-variabel kontinuu dengan label.

## Data Preparation
---
Tahap *data preparation* dilakukan untuk menyiapkan data agar dapat digunakan pada saat *modelling*. Berdasarkan proses *data understanding* sebelumnya, proses *data preparation* yang dilakukan antara lain:
- ***Feature Selection***. Proses ini dilakukan untuk mengambil/memilih variabel yang akan digunakan. Berdasarkan proses EDA, didapatkan kesimpulan bahwa hanya beberapa variabel yang memiliki kontribusi terhadap label.
- ***Train-Test-Split***. Proses ini dilakukan untuk membagi dataset menjadi data latih (*train*) dan data uji (*test*).
- ***Standardization***. Proses ini dilakukan untuk melakukan standarisasi terhadap data sehingga lebih mudah digunakan oleh model *machine learning*.

## Modeling
---
Tahap *modeling* dilakukan untuk mempersiapkan model *machine learning* yang akan digunakan. Dalam projek ini, 3 jenis model yang berbeda akan digunakan untuk mengetahui model yang memiliki performa terbaik untuk klasifikasi dataset *mobile price*. Ketiga model tersebut antara lain ***Logistic Regression***, ***SVM***, dan ***Random Forest***. Ketiga model ini digunakan tanpa melakukan *hyperparameter tuning* untuk mendapatkan *baseline model* terbaik diantara ketiganya.
#### Model Explanation
Model yang digunakan antara lain ***Logistic Regression***, ***SVM***, dan ***Random Forest***. Berikut merupakan pembahasan kelebihan dan kekurangan dari masing-masing model [[1]](https://towardsdatascience.com/pros-and-cons-of-various-classification-ml-algorithms-3b5bfb3c87d6)
1. **Logistic Regression**
   - Kelebihan
     - Mudah untuk diimplementasikan.
     - Tidak memerlukan *scaling* data.
     - Tidak memerlukan *hyperparameter tuning*.
   - Kekurangan
     - Memiliki performa buruk pada data linear (gambar).
     - Memiliki performa buruk pada data yang tidak relevan dan fitur yang memiliki korelasi tinggi.
     - Memiliki ketergantungan tinggi pada representasi data (fitur yang penting saja).
2. **SVM**
   - Kelebihan
     - Bekerja baik pada data dengan dimensi yang tinggi.
     - Algoritma terbaik pada data dengan kelas yang mudah dipisahkan (baik oleh garis lurus maupun non-linear).
     - *Outlier* tidak begitu berpengaruh pada performa.
     - SVM baik digunakan pada kasus klasifikasi biner yang ekstrim.
   - Kekurangan
     - Bekerja lambat pada dataset yang besar.
     - Tidak bekerja dengan baik pada kelas yang saling bertumpuk.
     - Diperlukan *hyperparameter tuning* yang tepat agar SVM bekerja dengan baik.
     - Menentukan kernel yang tepat cukup menantang.
3. **Random Forest**
   - Kelebihan
     - Tetap dapat bekerja dengan baik meski menggunakan variabel atau fitur yang saling berkorelasi.
     - Mampu mengurangi *error* yang muncul.
     - Performa yang baik pada data dengan *imbalanced class*.
     - Mampu bekerja dengan baik meski pada data dengan ukuran yang besar.
     - *Outlier* tidak mempengaruhi performa model secara signifikan.
     - Meminimalisir kemungkinan *overfitting*.
     - Dapat digunakan untuk *feature selection*
   - Kekurangan
     - Fitur yang digunakan harus memiliki *predictive power* (berkontribusi terhadap label).
     - Merupakan model *Black Box*.

Ketiga model ini diuji dan dibandingkan hasilnya pada proses *evaluation* berikut ini.
## Evaluation
---
Tahap *evaluation* bertujuan untuk melakukan pengujian terhadap performa model. Pada tahap ini, dilakukan pengujian terhadap beberapa metriks diantaranya **precision**, **recall**, **f1-score**, dan **accuracy**.

Masing-masing model dilatih tanpa melakukan *hyperparameter tuning* (selain memilih kernel untuk SVM). Model dilatih menggunakan data latih yang sama. Berikut merupakan hasil dari proses pelatihan model.
|           | Logistic Regression         | SVM      | Random Forest   |
|-----------|-----------------------------|----------|-----------------|
| Precision | **0.95**                    | **0.95** | 0.91            |
| Recall    | **0.95**                    | **0.95** | 0.92            |
| F1-Score  | **0.95**                    | **0.95** | 0.91            |
| Accuracy  | **0.95**                    | 0.94     | 0.92            |

Berdasarkan hasil pelatihan di atas, didapatkan bahwa model ***Logistic Regression*** memiliki performa terbaik sebagai *baseline model* untuk kasus klasifikasi *mobile price*.