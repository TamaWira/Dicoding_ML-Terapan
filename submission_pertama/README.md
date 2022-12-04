# Laporan Proyek Machine Learning - I Putu Bayu Adhya Wiratama

## Domain Proyek
---
Dewasa ini, teknologi tidak dapat lepas dari kehidupan manusia. Penggunaan teknologi dapat membantu kehidupan manusia menjadi lebih mudah, seperti dalam hal komunikasi, efisiensi produksi, dan lain-lain. Salah satu bentuk teknologi yang sangat membantu manusia saat ini adalah *Handphone* atau telepon genggam.

Hampir setiap orang di dunia ini memiliki *handphone* yang digunakan untuk berbagai keperluan, seperti komunikasi jarak jauh, mencari informasi, hingga hiburan. Sudah banyak jenis *handphone* yang beredar di pasaran dengan spesifikasinya masing-masing. Perbedaan spesifikasi ini membuat harga tiap *handphone* memiliki perbedaan [[1]](https://www.researchgate.net/publication/310597210_Factors_Affecting_Mobile_Phone_Brand_Preference_Empirical_Study_on_Sri_Lankan_University_Students). Perbedaan harga ini kemudian menimbulkan berbagai permasalahan, baik dari sisi penjualan bagi distributor *handphone*, maupun dari sisi *customer* yang ingin membeli *handphone*.

Kurangnya landasan yang baik dalam menentukan harga jual/beli *handphone* membuat pihak distributor tidak dapat menentukan harga jual/beli *handphone* dengan baik (menebak-nebak berdasarkan pengalaman dan harga pasar). Hal itu juga menyebabkan kurangnya kepercayaan konsumen/pembeli terhadap harga jual *handphone* yang telah ditetapkan oleh penjual. Untuk itu, penulis mencoba untuk menyelesaikan permasalahan tersebut menggunakan pendekatan ***Machine Learning*** untuk membuat perangkat lunak yang dapat menentukan kategori *range* harga jual/beli *handphone* berdasarkan spesifikasi yang dimilikinya.

Proyek ini bertujuan untuk melakukan klasifikasi kategori *range* harga *handphone* berdasarkan berbagai fitur atau spesifikasi yang dimilikinya. Dengan menggunakan spesifikasi *handphone* sebagai landasan dalam menentukan harga jual atau beli *handphone*, maka harga jual atau beli pun akan semakin akurat. Proyek ini mengangkat topik **Teknologi** dengan subbidang **klasifikasi**.

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

Berikut merupakan hasil dari masing-masing EDA yang dilakukan.
**1. Statistik Deskriptif**

Tabel 1. Statistik Deskriptif Dataset
|       | battery_power |      blue | clock_speed |    dual_sim | ... | price_range |
|-------|--------------:|----------:|------------:|------------:|-----|-------------|
| count |   2000.000000 | 2000.0000 | 2000.000000 | 2000.000000 | ... | 2000.000000 |
|  mean |   1238.518500 |    0.4950 |    1.522250 |    0.509500 | ... | 1.500000    |
|  std  |    439.418206 |    0.5001 |    0.816004 |    0.500035 | ... | 1.118314    |
|  min  |    501.000000 |    0.0000 |    0.500000 |    0.000000 | ... | 0.000000    |
|  25%  |    851.750000 |    0.0000 |    0.700000 |    0.000000 | ... | 0.750000    |
|  50%  |   1226.000000 |    0.0000 |    1.500000 |    1.000000 | ... | 1.500000    |
|  75%  |   1615.250000 |    1.0000 |    2.200000 |    1.000000 | ... | 2.250000    |
|  max  |   1998.000000 |    1.0000 |    3.000000 |    1.000000 | ... |    3.000000 |
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tabel 1 merupakan hasil dari statistik deskriptif dataset *Mobile Price*. Statistik deskriptif tersebut didapat dengan menggunakan fungsi `describe` yang terdapat pada object `DataFrame` dari *library* Pandas. Pada statistik deskriptif tersebut, kita dapat mengetahui informasi mengenai jumlah data, rata-rata (*mean*), standar deviasi (std), nilai minimum (*min*), kuartil bawah (25%), kuartil 2 atau nilai tengah (*median*), kuartil atas (75%), serta nilai maksimum (*max*) dari dataset. 

**2. Persebaran Data**
![Label Distribution](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/label%20distribution.png?token=GHSAT0AAAAAAB3GYHOKFVPC7PEOPU2NZ4UOY4MNYWQ)
Gambar 2. Persebaran Data pada Label
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gambar 2 merupakan hasil *plot* persebaran data pada label (`price_range`). *Plot* dilakukan dengan menggunakan *library* `seaborn` menggunakan fungsi `histplot`. Terlihat pada *plot* bahwa persebaran dari masing-masing data imbang (*balance*), yaitu masing-masing berjumlah 500 data.

![Variabel Biner_Blue](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/distribusi%20biner_blue.png?token=GHSAT0AAAAAAB3GYHOKM7Y4OPHD6WCIBICSY4MNYLA)
Gambar 3. Persebaran Data Variabel Biner '*blue*'

![Variabel Biner dual_sim](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/distribusi%20biner_dual-sim.png?token=GHSAT0AAAAAAB3GYHOLE2ZZNJ5NOPZ4YJWQY4MNZDQ)
Gambar 4. Persebaran Data Variabel Biner '*dual_sim*'

![Variabel Biner four_g](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/distribusi%20biner_four-g.png?token=GHSAT0AAAAAAB3GYHOKQPRKKLEOX7GFAJMWY4MNZMQ)
Gambar 5. Persebaran Data Variabel Biner '*four_g*'

![Variabel Biner three_g](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/distribusi%20biner_three-g.png?token=GHSAT0AAAAAAB3GYHOL4YYIAEW4U5OPYKQUY4MNZTQ)
Gambar 6. Persebaran Data Variabel Biner '*three_g*'

![Variabel Biner touchscreen](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/distribusi%20biner_touchscreen.png?token=GHSAT0AAAAAAB3GYHOL574QXWJLNFYM2F54Y4MNZ4A)
Gambar 7. Persebaran Data Variabel Biner '*touch_screen*'

![Variabel Biner wifi](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/distribusi%20biner_wifi.png?token=GHSAT0AAAAAAB3GYHOKSS5NPSJNKATATTWUY4MN2DQ)
Gambar 8. Persebaran Data Variabel Biner '*wifi*'

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gambar 3 hingga 8 merupakan hasil *plot* persebaran data pada variabel dengan tipe biner (hanya memiliki nilai 0 atau 1). Pada masing-masing *plot* tersebut, data masing-masing variabel tersebar secara rata pada masing-masing label. Hasil yang berbeda yaitu pada gambar 6 (distribusi variabel `three_g`), dimana data *handphone* yang memiliki fitur *3G* lebih banyak dibanding *handphone* yang tidak memiliki fitur *3G*. Namun, persebaran pada masing-masing label tetap imbang. Hal ini mengindikasikan bahwa variabel biner yang terdapat pada dataset *Mobile Phone* tidak memiliki kemampuan prediktif terhadap label. Berikut merupakan *plot* persebaran pada variabel numerik bertipe kontinuu.

**3. Persebaran Data Kontinuu**
![Pairplot](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/pairplot_numerik.png?token=GHSAT0AAAAAAB3GYHOKBJJUM64V2YFR3Y3OY4MN2OA)
Gambar 9. *Pairplot* Variabel Kontinuu
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gambar 9 merupakan hasil *pairplot* antar masing-masing variabel numerik bertipe kontinuu. *Pairplot* tersebut dihasilkan menggunakan bantuan fungsi `pairplot` yang terdapat pada *library* `seaborn`. *Pairplot* tersebut menunjukkan hasil *scatterplot* antar variabel yang dapat digunakan sebagai indikasi adanya korelasi antar variabel. Kita dapat mengetahui korelasi antar variabel independen dengan label (`price_range`) pada baris terbawah atau kolom terkanan. Dapat dilihat bahwa data pada masing-masing variabel tersebar secara merata pada masing-masing label kecuali variabel `ram`. Variabel `ram` memiliki korelasi positif terhadap label dimana semakin besar nilai ram dari sebuah *handphone*, maka harganya cenderung semakin tinggi. hal ini mengindikasikan korelasi positif yang cukup kuat antara variabel `ram` dengan label.

**4. Heatmap Korelasi**
![Heatmap](https://raw.githubusercontent.com/TamaWira/Dicoding_ML-Terapan/main/submission_pertama/assets/EDA/heatmap_corr.png?token=GHSAT0AAAAAAB3GYHOKFSJVN4XIWEBTCHN4Y4MN2WA)
Gambar 10. *Heatmap* Korelasi antar Variabel
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gambar 10 merupakan hasil dari *plot* korelasi antar masing-masing variabel numerik bertipe kontinuu. *Plot* tersebut dihasilkan menggunakan fungsi `heatmap` dari *library* `seaborn` untuk menghasilkan *heatmap* (peta suhu), dan fungsi `corr` yang terdapat pada *library* `Pandas` untuk mendapatkan korelasi masing-masing variabel. Dapat dilihat bahwa semakin terang warna dari kotak pada *heatmap*, maka semakin tinggi (positif) pula korelasinya. Pada *heatmap* tersebut, korelasi variabel independen yang paling tinggi dengan label adalah variabel `ram` yaitu mencapai nilai 0.9, yang artinya variabel `ram` memiliki korelasi positif yang kuat terhadap label. Hal ini selaras dengan temuan pada *pairplot* sebelumnya. Selain itu, terdapat beberapa variabel yang memiliki korelasi positif dengan label, diantaranya `battery_power` dengan nilai 0.2, `px_height` dengan nilai 0.1, serta `px_width` dengan nilai 0.2.

**Kesimpulan**: Berdasarkan hasil yang didapat pada proses EDA, didapatkan kesimpulan bahwa variabel yang memiliki kontribusi atau nilai prediktif terhadap label adalah variabel `ram`, `battery_power`, `px_height`, dan `px_width`. Variabel ini yang akan digunakan pada proses berikutnya hingga *modeling*.

## Data Preparation
---
Tahap *data preparation* dilakukan untuk menyiapkan data agar dapat digunakan pada saat *modelling*. Berdasarkan proses *data understanding* sebelumnya, proses *data preparation* yang dilakukan antara lain:
##### Feature Selection
*Feature Selection* merupakan proses yang dilakukan untuk mengambil/memilih variabel yang akan digunakan. Berdasarkan proses EDA, didapatkan kesimpulan bahwa hanya beberapa variabel yang memiliki kontribusi terhadap label. Berikut merupakan hasil *feature selection*.

Tabel 2. Hasil *Feature Selection*
|      | battery_power | px_height | px_width | ram  |
|------|---------------|-----------|----------|------|
| 1122 |          1871 |       275 |     1966 | 2727 |
| 1346 |          1446 |       351 |     1769 | 3340 |
| 1406 |          1731 |       142 |     1039 | 1220 |
| 1389 |          1801 |       100 |     1708 |  258 |
| 1534 |           622 |       760 |     1964 | 3183 |
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tabel 2 merupakan hasil dari *feature selection*. Proses *feature selection* bertujuan untuk mengambil variabel yang akan digunakan saja, diantaranya `ram`, `battery_power`, `px_height`, `px_width`, dan `price_range` (label).
##### Train-Test-Split.
Proses ini dilakukan untuk membagi dataset menjadi data latih (*train*) dan data uji (*test*). Proses *train test split* dilakukan dengan menggunakan bantuan dari fungsi `train_test_split` yang terdapat pada *library* `scikit-learn`. Pembagian data latih dan data uji adalah sebesar 8:2 (80% untuk data latih dan 20% untuk data uji). Proses ini menghasil dua (2) *subset* data dengan data latih sebesar 1600 data dan data uji sebesar 400 data.
##### Standardization
Proses ini dilakukan untuk melakukan standarisasi terhadap data sehingga lebih mudah digunakan oleh model *machine learning*. Proses ini dilakukan dengan menggunakan bantuan dari fungsi `StandardScaler` yang terdapat pada *library* `scikit-learn`. *Standardization* dilakukan pada data latih terlebih dahulu. Berikut merupakan hasil dari proses *Standardization*.

Tabel 3. Hasil *Standardization*
|      | battery_power | px_height |  px_width |       ram |
|-----:|--------------:|----------:|----------:|----------:|
| 1122 |      1.457735 | -0.838388 |  1.642181 |  0.566133 |
| 1346 |      0.491086 | -0.667549 |  1.186611 |  1.128347 |
| 1406 |      1.139309 | -1.137355 | -0.501540 | -0.816015 |
| 1389 |      1.298522 | -1.231766 |  1.045546 | -1.698315 |
| 1534 |     -1.383075 |  0.251831 |  1.637556 |  0.984354 |
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tabel 3 merupakan hasil dari proses *Standardization*. Proses tersebut mengubah data sehingga nilai *mean* dari data adalah 0 dan standar deviasi dari data adalah 1.

## Modeling
---
Tahap *modeling* dilakukan untuk mempersiapkan model *machine learning* yang akan digunakan. Dalam projek ini, 3 jenis model yang berbeda akan digunakan untuk mengetahui model yang memiliki performa terbaik untuk klasifikasi dataset *mobile price*. Ketiga model tersebut antara lain ***Logistic Regression***, ***SVM***, dan ***Random Forest***. Ketiga model ini digunakan tanpa melakukan *hyperparameter tuning* untuk mendapatkan *baseline model* terbaik diantara ketiganya.

### Model Explanation
Model yang digunakan antara lain ***Logistic Regression***, ***SVM***, dan ***Random Forest***. Berikut merupakan pembahasan dari masing-masing model, termasuk kelebihan dan kekurangannya.

#### 1. Logistic Regression
*Logistic Regression* dinamai sesuai fungsi yang digunakan pada intinya, fungsi logistik. Ahli statistik awalnya menggunakannya untuk menggambarkan sifat pertumbuhan populasi. Fungsi sigmoid dan fungsi logit adalah beberapa variasi dari fungsi logistik. Fungsi logit adalah kebalikan dari fungsi logistik standar. 

Pada proyek ini, tidak ada parameter yang digunakan pada model selain parameter *default*.

Berikut merupakan kelebihan serta kekurangan dari model/algoritma *Logistic Regression*.
**Kelebihan**
- Mudah untuk diimplementasikan.
- Tidak memerlukan *scaling* data.
- Tidak memerlukan *hyperparameter tuning*.

**Kekurangan**
 - Memiliki performa buruk pada data linear (gambar).
 - Memiliki performa buruk pada data yang tidak relevan dan fitur yang memiliki korelasi tinggi.
 - Memiliki ketergantungan tinggi pada representasi data (fitur yang penting saja).

#### 2. SVM
SVM (*Support Vector Machine*) merupakan sebuah algoritma *machine learning* yang bertujuan untuk menciptakan sebuah garis yang memisahkan antar kelas (disebut *hyperplane*). *Hyperplane* bertujuan untuk memisahkan antar kelas berdasarkan *margin* dengan mengukur jarak terbesar antara *hyperplane* dengan data yang berada pada titik terluar dari masing-masing label (*support vector*).

Pada proyek ini, parameter yang digunakan pada model (selain parameter *default*) adalah tipe kernel yaitu `linear`.

Berikut merupakan kelebihan serta kekurangan dari model/algoritma *SVM*.
**Kelebihan**
 - Bekerja baik pada data dengan dimensi yang tinggi.
 - Algoritma terbaik pada data dengan kelas yang mudah dipisahkan (baik oleh garis lurus maupun non-linear).
 - *Outlier* tidak begitu berpengaruh pada performa.
 - SVM baik digunakan pada kasus klasifikasi biner yang ekstrim.

**Kekurangan**
 - Bekerja lambat pada dataset yang besar.
 - Tidak bekerja dengan baik pada kelas yang saling bertumpuk.
 - Diperlukan *hyperparameter tuning* yang tepat agar SVM bekerja dengan baik.
 - Menentukan kernel yang tepat cukup menantang.

#### 3. Random Forest
*Random Forest* merupakan salah satu model *machine learning* dengan jenis *ensemble*. Model *ensemble* merupakan model *machine learning* yang tersusun dari banyak model *machine learning* individual. Dalam hal ini, *random forest* tersusun dari banyak model *decision tree* individual yang saling independen. *Random Forest* menerapkan konsep *Bagging* atau *Bootstap Aggregating*, dimana akan diciptakan *n* buah subsampel data dari keseluruhan data yang utuh. Subsampel data ini kemudian akan digunakan oleh masing-masing model *decision tree* untuk dilakukan prediksi atau klasifikasi. Hasil dari masing-masing *decision tree* kemudian akan dilakukan *voting* (*aggregating*) untuk mendapatkan hasil terbanyak. Hasil dari *voting* ini yang akan menjadi hasil keluaran dari model *random forest*.

Pada proyek ini, tidak ada parameter yang digunakan pada model selain parameter *default*.

Berikut merupakan kelebihan dan kekurangan dari model/algoritma *Random Forest*.
**Kelebihan**
 - Tetap dapat bekerja dengan baik meski menggunakan variabel atau fitur yang saling berkorelasi.
 - Mampu mengurangi *error* yang muncul.
 - Performa yang baik pada data dengan *imbalanced class*.
 - Mampu bekerja dengan baik meski pada data dengan ukuran yang besar.
 - *Outlier* tidak mempengaruhi performa model secara signifikan.
 - Meminimalisir kemungkinan *overfitting*.
 - Dapat digunakan untuk *feature selection*

**Kekurangan**
 - Fitur yang digunakan harus memiliki *predictive power* (berkontribusi terhadap label).
 - Merupakan model *Black Box*.

Ketiga model ini diuji dan dibandingkan hasilnya pada proses *evaluation* berikut ini.

## Evaluation
---
Tahap *evaluation* bertujuan untuk melakukan pengujian terhadap performa model. Pada tahap ini, dilakukan pengujian terhadap beberapa metriks diantaranya **precision**, **recall**, **f1-score**, dan **accuracy**.

Berikut merupakan penjelasan dari masing-masing metriks yang digunakan.
#### 1. Precision
*Precision* berfokus pada prediksi positif. *Precision* adalah rasio prediksi positif yang benar terhadap semua prediksi positif. *Prediction* mengevaluasi model hanya berdasarkan prediksi positif. Berikut merupakan formula dari metriks *precision*.
$$ precision = TP \over {TP + FP} $$

#### 2. Recall
*Recall* adalah rasio prediksi positif yang benar terhadap semua observasi di kelas positif. Dengan demikian, model dievaluasi berdasarkan kemampuannya untuk memprediksi kelas positif. Berikut merupakan formula dari metriks *recall*.
$$ recall = TP \over {TP + FN} $$

#### 3. F1-Score
*F1-Score* adalah rata-rata tertimbang dari *precision* dan *recall*. **1-Score* adalah ukuran yang lebih berguna daripada akurasi untuk masalah dengan distribusi kelas yang tidak merata karena memperhitungkan positif palsu dan negatif palsu. Berikut merupakan formula dari metriks *f1-score*.
$$ F1_score = 2 \times {precision * recall} \over {precision + recall} $$

#### 4. Accuracy
Akurasi merupakan metriks yang menghitung rasio jumlah prediksi yang benar dengan jumlah semua prediksi. Jika model memprediksi dengan benar 90 pengamatan (yaitu titik data) dari 100, akurasi klasifikasi adalah 90%. Formula dari metriks akurasi adalah sebagai berikut.
$$ accuracy = Number of correct predictions \over Number of all predictions $$

Berikut merupakan hasil dari proses evaluasi model.

Tabel 4. Hasil Evaluasi Performa Model Machine Learning
|           | Logistic Regression         | SVM      | Random Forest   |
|-----------|-----------------------------|----------|-----------------|
| Precision | **0.95**                    | **0.95** | 0.91            |
| Recall    | **0.95**                    | **0.95** | 0.92            |
| F1-Score  | **0.95**                    | **0.95** | 0.91            |
| Accuracy  | **0.95**                    | 0.94     | 0.92            |
Tabel 4 merupakan hasil evaluasi performa dari masing-masing model *machine learning* merupakan data uji (*test*). Berdasarkan hasil tersebut, didapatkan bahwa model ***Logistic Regression*** memiliki performa terbaik sebagai *baseline model* untuk kasus klasifikasi *mobile price*.

## Conclusion
---
Klasifikasi *Mobile Price Dataset* bertujuan untuk melakukan prediksi terhadap kategori *range* harga *handphone* atau telepon genggam berdasarkan beberapa spesifikasi yang dimilikinya. Berdasarkan proses *Exploratory Data Analysis*, didapatkan bahwa variabel yang memiliki kontribusi atau kemampuan prediktif terhadap label adalah `ram`, `battery_power`, `px_height`, dan `px_width`. Variabel-variabel ini digunakan untuk proses prediksi. Pada tahap *Data Preparation*, dilakukan *feature selection* untuk mengambil variabel yang digunakan saja, setelah itu dilakukan *train test split* untuk membagi dataset menjadi data latih dengan proporsi 80% dan data uji dengan proporsi 20%. Proses *Standardization* dilakukan untuk melakukan normalisasi terhadap data. Data yang telah dipersiapkan kemudian digunakan pada proses *training* dan *evaluation model* menggunakan beberapa model sebagai perbandingan, diantaranya *Logistic Regression*, SVM, dan *Random Forest*. Setelah melakukan proses evaluasi, didapatkan bahwa model *Logistic Regression* mendapatkan hasil terbaik, yaitu 95% pada masing-masing metriks. Oleh karena itu, model ***Logistic Regression*** digunakan sebagai model *baseline* untuk kasus klasifikasi *mobile price dataset*.