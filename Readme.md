# *Extreme Learninng Machine* (ELM)

Algoritma *Extreme Learning Machine* (ELM) merupakan algoritma jaringan saraf tiruan yang tergolong baru. Algoritma ini dikenalkan oleh Huang, dkk pada tahun 2004 dalam sebuah jurnal yang berjudul “*Extreme Learning Machine: A New Learning Scheme of Feedforward Neural Networks*”. Algoritma ini berusaha mengatasi masalah yang dialami algoritma jaringan saraf tiruan sebelumnya, yaitu dalam hal kecepatan belajar. Adanya *epoch* atau perulangan untuk melakukan pembelajaran dalam berbagai algoritma terdahulu membuat kecepatan pembelajaran menjadi lambat.ELM hadir dengan menggunakan konsep *Single Hidden Layer Feedforward Neural Network* (SLFNs) yang berarti arsitekturnya hanya menggunakan satu *hidden layer*. Proses pelatihan dalam ELM tidak menggunakan *epoch* dan minimalisasi error sehingga prosesnya berlangsung cukup cepat. Dalam ELM inisialisasi bobot dan bias dilakukan secara acak. Tahapan dalam melakukan klasifikasi dengan menggunakan ELM adalah sebagai berikut:
1. *Exploratory Data*
2. *Preprocessing Data*
3. Proses Pelatihan
4. Proses Pengujian
# *Dataset*

Dataset yang digunakan dalam jurnal ini adalah iris plant dataset dari UCI Machine Learning Repository. Dataset ini berisi klasifikasi bunga iris berdasarkan 4 fitur yaitu petal length, petal width, sepal length, dan sepal width. Terdapat tiga kelas target yaitu iris virginica, iris setosa dan iris versicolor. Setiap kelas mempunyai 50 buah data.
![image](https://user-images.githubusercontent.com/68947748/207584776-2e953d14-a3c1-4d72-a9ff-14a45da38a53.png)
# Exploratory Data

Exploratory adalah kegiatan untuk mengenali data menggunakan serangkaian metode analisis (Yunita. 2021). Kegiatan ini bertujuan untuk memahami pola data, menemukan anomali, dan menentukan proses *preprocessing* yang harus dilakukan untuk mempersiapkan data. Proses *exploratory* data yang dilakukan adalah sebagai berikut: 
a. Membuat ringkasan numerik dari data
b. Menemukan anomali data seperti *missing value, duplicate value* dan *outlier*
# *Preprocessing Data*

*Preprocessing* data adalah tahapan yang dilakukan untuk mempersiapkan data agar siap untuk dimasukkan ke dalam algoritma. *Preprocessing* data dilakukan dengan melakukan pembersihan data, seperti penghilangan *missing value, duplicate value,* *outlier* dan normalisasi data.Normalisasi data dilakukan dengan menggunakan *min-max scaler.* Normalisasi data dilakukan dengan persamaan:
Xscaled=X-Xmin / Xmax-Xmin			    
Xscaled	= data hasil *scaling*
X			  = data
X min	   = nilai minimal data
Xmax   	= nilai maksimal data

# Proses Pelatihan

Proses pelatihan adalah tahapan untuk melakukan memasukkan data yang telah dipersiapkan ke model. Data dibagi menjadi 70% data latih dan 30% data uji. Proses pelatihan berguna untuk mendapatkan nilai bobot yang optimal (Alfiyatin et al. 2019). Tahapan pelatihan dalam ELM adalah sebagai berikut (Alfiyatin et al. 2019):

1. Membuat matriks W berukuran mn dengan rentang nilai 0-1 secara random. Nilai m adalah jumlah hidden neuron dan n adalah jumlah input neuron. W merupakan matriks bobot awal. 
2. Menghitung matriks inisialisasi hidden layer dengan menggunakan persamaan 
Hinit= X . WT			    
Hinit	= matriks inisialisasi hidden layer
*X*	= matriks input data latih
WT	= transpose matriks bobot
3. Menghitung matriks keluaran hidden layer dengan persamaan
H = 11+e-Hinit			    
*H* 	= matriks keluaran hidden layer
Hinit	= matriks inisialisasi hidden layer
4. Menghitung nilai H+ yang merupakan matriks *moore–penrose pseudo inverse.* Matriks H+ didapatkan dari persamaan
H+ =(HT.H)-1.HT		 
H+	= matriks moore–penrose pseudo inverse
*H*	= matriks keluaran hidden layer
HT	= transpose matriks keluaran hidden layer
5. Menghitung nilai bobot keluaran (B) dengan menggunakan persamaan 
B= H+. Y			    
B = matriks bobot keluaran
H+	= matriks moore–penrose pseudo inverse
*Y*	= matriks label/target
6. Menghitung nilai output dengan menggunakan persamaan 
y = H**B*	    
*y*	= nilai output
*H*	= matriks keluaran hidden layer 	
B = matriks bobot keluaran

# 	Proses Pengujian

Proses *testing* dilakukan untuk melakukan prediksi berdasarkan nilai bobot yang diperoleh pada proses pelatihan. Tahapan proses *testing* sama dengan proses pelatihan, tetapi melakukan perhitungan karena sudah dilakukan pada proses pelatihan. Tahapan *testing* adalah sebagai berikut (Sugianto et al. 2018)
1. Menghitung nilai matriks inisialisasi hidden layer dengan menggunakan persamaan 

2. Menghitung matriks keluaran hidden layer dengan persamaan 

3. Menghitung nilai output dengan menggunakan persamaan 

4. Membulatkan nilai hasil prediksi dengan menggunakan persamaan
   *y = round(x)*
   *y*	*=* hasil pembulatan prediksi
   *x*	= nilai prediksi

5. Menghitung nilai akurasi dengan menggunakan persamaan 
     *acc =* *jumlah prediksi benar* / *jumlah prediksi*

6. Menghitung nilai RMSE dengan persamaan

     ![image](https://user-images.githubusercontent.com/68947748/207589657-dba312ca-fcc4-43b5-be32-57733cc9c516.png)



# Hasil dan Analisis

Pada proses pelatihan digunakan parameter jumlah *hidden neuron* yang bereda beda. Nilai jumlah *hidden neuron* yang digunakan adalah 1-15. Gambar 1. menunjukkan grafik akurasi hasil pengujian jumlah neuron. Gambar 2. menunjukkan grafik RMSE hasil pengujian jumlah neuron. 

![image](https://user-images.githubusercontent.com/68947748/207590536-d4807cad-480d-4f9e-9227-603c972252e7.png)

![image](https://user-images.githubusercontent.com/68947748/207590570-4917ac61-357c-4290-8824-a7075a97113d.png)

Berdasarkan 1 dan 2 di atas, jumlah *hidden neuron* yang menghasilkan akurasi tertinggi dan RMSE paling rendah adalah 5 buah *hidden neuron.* Akurasi yang dihasilkan ketika menggunakan 5 buah hidden neuron mencapai 1 atau 100%, sedangkan nilai RMSE adalah 0. Hal ini berarti model ELM mampu melakukan klasifikasi dengan baik dari data berdasarkan pada bobot pelatihan. Waktu yang digunakan untuk pelatihan juga sangat singkat yakni 0.000269 detik.

# Kesimpulan

Berdasarkan hasil dari percobaan, ELM adalah algoritma jaringan syaraf tiruan yang sangat handal. Algoritma ini mampu melakukan klasifikasi dengan hasil yang sangat baik dan dalam waktu yang sangat singkat. ELM mampu melakukan klasifikasi data Bunga Iris dengan akurasi mencapai 100% dengan menggunakan 5 buah *hidden neuron*. Waktu yang diperlukan untuk proses pelatihan juga sangat cepat yakni 0.000269 detik.	Di sisi lain algoritma ELM mempunyai kelemahan. Tingkat akurasi dari algoritma sangat bergantung kepada jumlah *hidden neuron* sehingga diperlukan percobaan dengan memanipulasi jumlah *hidden neuron*. Selain itu, akurasi juga sangat bergantung kepada inisialisasi bobot random di awal. Akurasi akan berubah-ubah ketika model dijalankan ulang karena bobot awal selalu berubah. Berdasarkan beberapa kelemahan di atas, perlu dilakukan pengembangan mengenai penentuan jumlah hidden neuron yang digunakan secara otomatis sehingga mampu menghasilkan akurasi yang baik. Selain itu juga perlu pengembangan mengenai proses random bobot awal sehingga proses pelatihan berulang tidak mengalami perubahan yang cukup signifikan.

# Daftar Pustaka

ALFIYATIN, A.N., MAHMUDY, W.F., ANANDA, C.F., & ANGGODO, Y.F., 2019. Penerapan Extreme Learning Machine (ELM) untuk Peramalan Laju Inflasi Di Indonesia. Jurnal Teknologi Informasi dan Ilmu Komputer. 6(2), pp.179-186.

NUR ALFIYATIN, A., FIRDAUS MAHMUDY, W., FAJRI ANANDA, C. AND PRIYO ANGGODO, Y., 2019. Penerapan Extreme Learning Machine (ELM) untuk Peramalan Laju Inflasi di Indonesia. Jurnal Teknologi Informasi dan Ilmu Komputer, [online] 6(2), pp.179–186. https://doi.org/10.25126/JTIIK.201962900.
