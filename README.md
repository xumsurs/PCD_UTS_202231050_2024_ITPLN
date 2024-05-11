# PCD_UTS_202231050_2024_ITPLN

import cv2
import matplotlib.pyplot as plt # memvisualisasi data
import numpy as np # membaca angka
Kode tersebut merupakan script Python yang menggunakan library `cv2` (OpenCV), `matplotlib.pyplot` (matplotlib), dan `numpy`. Ini digunakan untuk pemrosesan gambar, termasuk membaca, memanipulasi, dan memvisualisasikan gambar.

img = cv2.imread("uts pengcit.jpg")
Baris kode tersebut menggunakan OpenCV untuk membaca sebuah gambar yang disimpan dalam file "uts pengcit.jpg" menjadi sebuah array NumPy yang merepresentasikan piksel-piksel dalam gambar.

img.shape # membuat variabel dalam baris dan kolom dalam shape citra

[baris, kolom] = img.shape[:2]
Baris kode tersebut mengambil dimensi tinggi (baris) dan lebar (kolom) dari gambar yang telah dibaca sebelumnya menggunakan OpenCV.

img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
Baris kode tersebut mengubah skema warna gambar dari BGR (Blue, Green, Red) ke RGB (Red, Green, Blue) menggunakan fungsi `cv2.cvtColor()` dari OpenCV.

plt.imshow(img)
menampilkan 

alpa = 1.2
beta = 10

citra = np.zeros((baris, kolom, 3))

for x in range (baris) :
    for y in range (kolom) :
        gcx = (img[x, y] * alpa) + beta
        citra[x, y] = gcx

citra = citra.astype(np.uint8)
Kode tersebut melakukan penyesuaian kontras dan kecerahan pada gambar yang telah dibaca sebelumnya. Dengan menggunakan variabel `alpa` dan `beta` untuk mengontrol kontras dan kecerahan, setiap piksel gambar diubah sesuai rumus penyesuaian kontras dan kecerahan, kemudian disimpan dalam array `citra`.

# menampilkan
fig, axs = plt.subplots(2, 2, figsize = (15, 5))
axs[0, 0].imshow(img)
axs[0, 1].hist(img.ravel(), 256, [0, 256])
axs[1, 0].imshow(citra)
axs[1, 1].hist(citra.ravel(), 256, [0, 256])
plt.show()

plt.subplot(2, 2, 1)
plt.imshow(citra)
plt.title('Original Image')
Kode tersebut menampilkan gambar asli, histogramnya, gambar hasil penyesuaian kontras dan kecerahan, serta histogramnya dalam satu tampilan yang terorganisir. Ini dilakukan dengan memanfaatkan matplotlib.

# Display the red channel
plt.subplot(2, 2, 2)
plt.imshow(citra[:,:,0], cmap="gray")
plt.title('Red Channel')
Kode tersebut menampilkan saluran warna merah (red channel) dari gambar hasil penyesuaian kontras dan kecerahan (`citra`). Ini ditampilkan dalam subplot yang baru dengan judul "Red Channel".

# Display the green channel
plt.subplot(2, 2, 3)
plt.imshow(citra[:,:,1], cmap="gray")
plt.title('Green Channel')
Kode tersebut menampilkan saluran warna hijau (green channel) dari gambar hasil penyesuaian kontras dan kecerahan (`citra`). Ini ditampilkan dalam subplot yang baru dengan judul "Green Channel".

# Display the blue channel
plt.subplot(2, 2, 4)
plt.imshow(citra[:,:,2], cmap="gray")
plt.title('Blue Channel')
Kode tersebut menampilkan saluran warna biru (blue channel) dari gambar hasil penyesuaian kontras dan kecerahan (`citra`). Ini ditampilkan dalam subplot yang baru dengan judul "Blue Channel".

plt.show()
menampilkan

fig, axs = plt.subplots(3, 2, figsize=(15, 15))
Kode tersebut membuat grid subplot dengan ukuran 3x2 (3 baris, 2 kolom) dengan menggunakan `plt.subplots()`. Ukuran keseluruhan figure ditentukan sebagai 15x15 inci.

# Merah
merah = citra[:, :, 0]
hist_merah = cv2.calcHist([merah], [0], None, [256], [0, 256])
axs[0, 0].imshow(merah, cmap='gray')
axs[0, 0].set_title('Merah')
axs[0, 1].plot(hist_merah, color='r')
axs[0, 1].set_title('Histogram Merah')
Kode tersebut mengambil saluran warna merah dari gambar hasil penyesuaian kontras dan kecerahan (`citra`) dan menghitung histogramnya. Kemudian, gambar serta histogram saluran warna merah ditampilkan dalam subplot pertama dan kedua secara berurutan.

# Hijau
hijau = citra[:, :, 1]
hist_hijau = cv2.calcHist([hijau], [0], None, [256], [0, 256])
axs[1, 0].imshow(hijau, cmap='gray')
axs[1, 0].set_title('Hijau')
axs[1, 1].plot(hist_hijau, color='g')
axs[1, 1].set_title('Histogram Hijau')
Kode tersebut mengambil saluran warna hijau dari gambar hasil penyesuaian kontras dan kecerahan (`citra`) dan menghitung histogramnya. Kemudian, gambar serta histogram saluran warna hijau ditampilkan dalam subplot ketiga dan keempat secara berurutan.

# Biru
biru = citra[:, :, 2]
hist_biru = cv2.calcHist([biru], [0], None, [256], [0, 256])
axs[2, 0].imshow(biru, cmap='gray')
axs[2, 0].set_title('Biru')
axs[2, 1].plot(hist_biru, color='b')
axs[2, 1].set_title('Histogram Biru')

plt.tight_layout()
plt.show()
Kode tersebut melakukan hal serupa dengan kode sebelumnya, namun kali ini untuk saluran warna biru (blue channel):

1. `biru = citra[:, :, 2]`: Mengambil saluran warna biru (blue channel) dari gambar hasil penyesuaian kontras dan kecerahan (`citra`). Ini dilakukan dengan menggunakan indeks `[2]` pada sumbu ke-3 dari array `citra`, yang mewakili saluran warna biru.

2. `hist_biru = cv2.calcHist([biru], [0], None, [256], [0, 256])`: Menghitung histogram dari saluran warna biru yang telah diambil sebelumnya (`biru`) menggunakan fungsi `cv2.calcHist()`.

3. `axs[2, 0].imshow(biru, cmap='gray')`: Menampilkan saluran warna biru dalam subplot kelima (baris 2, kolom 0) menggunakan `imshow()`. Argumen `cmap='gray'` digunakan untuk menampilkan gambar dengan skala warna abu-abu.

4. `axs[2, 0].set_title('Biru')`: Memberikan judul "Biru" pada gambar yang ditampilkan di subplot kelima.

5. `axs[2, 1].plot(hist_biru, color='b')`: Menampilkan histogram saluran warna biru dalam subplot keenam (baris 2, kolom 1) menggunakan `plot()`. Argumen `color='b'` digunakan untuk memberikan warna biru pada plot histogram.

6. `axs[2, 1].set_title('Histogram Biru')`: Memberikan judul "Histogram Biru" pada plot histogram yang ditampilkan di subplot keenam.


# Konversi citra ke dalam ruang warna HSV
hsv_image = cv2.cvtColor(citra_gabungan, cv2.COLOR_RGB2HSV)
Baris kode tersebut menggunakan fungsi `cv2.cvtColor()` dari OpenCV untuk mengubah skema warna gambar `citra_gabungan` dari RGB (Red, Green, Blue) ke HSV (Hue, Saturation, Value). HSV adalah model warna yang merepresentasikan warna dalam bentuk tiga komponen: Hue (warna), Saturation (kejenuhan), dan Value (nilai kecerahan). Ini sering digunakan dalam pemrosesan gambar karena memudahkan untuk memanipulasi warna dan mendeteksi objek berdasarkan warna.

Argumen pertama dari `cv2.cvtColor()` adalah gambar yang akan diubah warnanya (`citra_gabungan`), dan argumen kedua adalah konstanta `cv2.COLOR_RGB2HSV`, yang menentukan konversi dari skema warna RGB ke skema warna HSV.

Setelah menjalankan baris kode tersebut, variabel `hsv_image` akan berisi gambar dengan skema warna yang telah diubah menjadi HSV.

# Definisikan rentang warna untuk setiap warna
lower_blue = np.array([100, 100, 100])
upper_blue = np.array([140, 255, 255])
Kode tersebut mendefinisikan rentang warna biru dalam skema warna HSV yang akan digunakan untuk mendeteksi warna biru dalam gambar. Rentang warna ini didefinisikan dalam bentuk array NumPy.

- `lower_blue`: Array NumPy yang menentukan nilai minimum untuk setiap komponen warna dalam skema HSV. Nilai-nilai ini menentukan batas bawah rentang warna biru yang ingin dideteksi. Urutannya adalah [Hue, Saturation, Value].
- `upper_blue`: Array NumPy yang menentukan nilai maksimum untuk setiap komponen warna dalam skema HSV. Nilai-nilai ini menentukan batas atas rentang warna biru yang ingin dideteksi. Urutannya juga [Hue, Saturation, Value].


# Gunakan ambang batas untuk warna hijau yang telah Anda temukan
lower_green = np.array([20, 100, 100])
upper_green = np.array([250, 255, 255])
Kode tersebut mendefinisikan rentang warna hijau dalam skema warna HSV yang akan digunakan untuk mendeteksi warna hijau dalam gambar. Rentang warna ini didefinisikan dalam bentuk array NumPy.

- `lower_green`: Array NumPy yang menentukan nilai minimum untuk setiap komponen warna dalam skema HSV. Nilai-nilai ini menentukan batas bawah rentang warna hijau yang ingin dideteksi. Urutannya adalah [Hue, Saturation, Value].
- `upper_green`: Array NumPy yang menentukan nilai maksimum untuk setiap komponen warna dalam skema HSV. Nilai-nilai ini menentukan batas atas rentang warna hijau yang ingin dideteksi. Urutannya juga [Hue, Saturation, Value].


lower_red1 = np.array([0, 100, 100])
upper_red1 = np.array([10, 255, 255])
lower_red2 = np.array([160, 100, 100])
upper_red2 = np.array([180, 255, 255])
Kode tersebut mendefinisikan rentang warna merah dalam skema warna HSV yang akan digunakan untuk mendeteksi warna merah dalam gambar. Rentang warna ini didefinisikan dalam bentuk array NumPy.

Untuk warna merah, seringkali rentang nilai hue (H) membutuhkan dua range karena rentang warna merah melintasi batas 0 dan 180 di dalam skala HSV. Oleh karena itu, kita perlu mendefinisikan dua rentang untuk mendeteksi warna merah dengan benar.

- `lower_red1` dan `upper_red1`: Array NumPy yang menentukan rentang nilai minimum dan maksimum untuk komponen hue (H) dalam skema HSV. Rentang ini mencakup rentang dari 0 hingga 10, yang mencakup bagian merah di sekitar nada 0 (merah murni).
- `lower_red2` dan `upper_red2`: Array NumPy yang menentukan rentang nilai minimum dan maksimum untuk komponen hue (H) dalam skema HSV. Rentang ini mencakup rentang dari 160 hingga 180, yang juga mencakup bagian merah di sekitar nada 0 (merah murni) yang melintasi batas 0 dan 180.

# Deteksi warna biru
mask_blue = cv2.inRange(hsv_image, lower_blue, upper_blue)
# Deteksi warna hijau
mask_green = cv2.inRange(hsv_image, lower_green, upper_green)
# Deteksi warna merah
mask_red1 = cv2.inRange(hsv_image, lower_red1, upper_red1)
mask_red2 = cv2.inRange(hsv_image, lower_red2, upper_red2)
mask_red = cv2.bitwise_or(mask_red1, mask_red2)
Kode tersebut melakukan deteksi warna dalam gambar berdasarkan rentang warna yang telah ditentukan sebelumnya dalam skema warna HSV.

- `cv2.inRange(hsv_image, lower_blue, upper_blue)`: Ini menghasilkan mask (gambar biner) yang menunjukkan di mana warna biru terdeteksi dalam gambar berdasarkan rentang warna yang ditentukan oleh `lower_blue` dan `upper_blue`.
  
- `cv2.inRange(hsv_image, lower_green, upper_green)`: Ini menghasilkan mask (gambar biner) yang menunjukkan di mana warna hijau terdeteksi dalam gambar berdasarkan rentang warna yang ditentukan oleh `lower_green` dan `upper_green`.

- `cv2.inRange(hsv_image, lower_red1, upper_red1)`: Ini menghasilkan mask (gambar biner) yang menunjukkan di mana warna merah (bagian 1) terdeteksi dalam gambar berdasarkan rentang warna yang ditentukan oleh `lower_red1` dan `upper_red1`.

- `cv2.inRange(hsv_image, lower_red2, upper_red2)`: Ini menghasilkan mask (gambar biner) yang menunjukkan di mana warna merah (bagian 2) terdeteksi dalam gambar berdasarkan rentang warna yang ditentukan oleh `lower_red2` dan `upper_red2`.

- `cv2.bitwise_or(mask_red1, mask_red2)`: Ini menggabungkan dua mask merah menjadi satu mask dengan operasi bitwise OR (`|`), sehingga kita memiliki mask tunggal yang menunjukkan di mana warna merah terdeteksi dalam gambar.

# Plot hasil

#gambar 1
gray = cv2.cvtColor(citra_gabungan, cv2.COLOR_RGB2GRAY)
fig, axs = plt.subplots (2, 2, figsize=(10,10))

(thresh, binary1) = cv2.threshold(gray, 0, 0, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')
Kode tersebut bertujuan untuk menghasilkan gambar biner (hitam putih) dari gambar gabungan dalam skala abu-abu (`gray`). Berikut penjelasan singkatnya:

1. `gray = cv2.cvtColor(citra_gabungan, cv2.COLOR_RGB2GRAY)`: Mengonversi gambar gabungan (`citra_gabungan`) dari skema warna RGB ke skema warna abu-abu (grayscale) menggunakan fungsi `cv2.cvtColor()`.

2. `(thresh, binary1) = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)`: Menerapkan ambang biner ke gambar abu-abu. Nilai piksel di bawah ambang (127) akan menjadi hitam (0), dan di atas ambang akan menjadi putih (255), sesuai dengan mode `cv2.THRESH_BINARY`.

3. `axs[0,0].imshow(binary1, cmap = 'gray')`: Menampilkan gambar biner yang dihasilkan dalam subplot pertama (baris 0, kolom 0) menggunakan `imshow()` dengan skala warna abu-abu.

4. `axs[0,0].set_title('BINARY')`: Memberikan judul "BINARY" pada plot yang ditampilkan di subplot pertama.


#gambar 2
plt.subplot(2, 2, 2)
plt.imshow(mask_blue, cmap='gray')
plt.title('Blue')
plt.xticks(np.arange(0, mask_blue.shape[1]+1, 800))
plt.yticks(np.arange(0, mask_blue.shape[0]+1, 500))
plt.axis('on')
Kode tersebut bertujuan untuk menampilkan hasil deteksi warna biru dalam bentuk mask (gambar biner) dalam subplot kedua dari grid 2x2. Berikut penjelasan singkatnya:

1. `plt.subplot(2, 2, 2)`: Menentukan subplot kedua dari grid 2x2 untuk menampilkan hasil deteksi warna biru.

2. `plt.imshow(mask_blue, cmap='gray')`: Menampilkan mask warna biru dalam skala abu-abu menggunakan `imshow()`.

3. `plt.title('Blue')`: Memberikan judul "Blue" pada gambar yang ditampilkan di subplot kedua.

4. `plt.xticks(np.arange(0, mask_blue.shape[1]+1, 800))` dan `plt.yticks(np.arange(0, mask_blue.shape[0]+1, 500))`: Mengatur label sumbu x dan y untuk menampilkan tick mark setiap 800 piksel (x) dan 500 piksel (y) untuk memudahkan dalam mengevaluasi posisi piksel pada gambar.

5. `plt.axis('on')`: Menampilkan sumbu pada gambar.


#gambar 3
plt.subplot(2, 2, 3)
plt.imshow(np.maximum(mask_red, mask_blue), cmap='gray')
plt.title('reed-blue')
plt.xticks(np.arange(0, mask_green.shape[1], 800))
plt.yticks(np.arange(0, mask_green.shape[0], 500))
plt.axis('on')
Kode tersebut bertujuan untuk menampilkan hasil gabungan dari deteksi warna merah dan biru dalam bentuk mask (gambar biner) dalam subplot ketiga dari grid 2x2. Berikut penjelasan singkatnya:

1. `plt.subplot(2, 2, 3)`: Menentukan subplot ketiga dari grid 2x2 untuk menampilkan hasil gabungan dari deteksi warna merah dan biru.

2. `plt.imshow(np.maximum(mask_red, mask_blue), cmap='gray')`: Menampilkan gabungan dari mask warna merah dan biru menggunakan operasi bitwise maximum (`np.maximum()`) untuk mendapatkan piksel-piksel yang terdeteksi sebagai merah atau biru. Hasilnya kemudian ditampilkan dalam skala abu-abu menggunakan `imshow()`.

3. `plt.title('reed-blue')`: Memberikan judul "reed-blue" pada gambar yang ditampilkan di subplot ketiga.

4. `plt.xticks(np.arange(0, mask_green.shape[1], 800))` dan `plt.yticks(np.arange(0, mask_green.shape[0], 500))`: Mengatur label sumbu x dan y untuk menampilkan tick mark setiap 800 piksel (x) dan 500 piksel (y) untuk memudahkan dalam mengevaluasi posisi piksel pada gambar.

5. `plt.axis('on')`: Menampilkan sumbu pada gambar.



#gambar 4
plt.subplot(2, 2, 4)
plt.imshow(mask_green, cmap='gray')
plt.title('Green')
plt.xticks(np.arange(0, mask_green.shape[1], 800))
plt.yticks(np.arange(0, mask_green.shape[0], 500))
plt.axis('on')
Kode ini menampilkan hasil deteksi warna hijau dalam bentuk mask (gambar biner) dalam subplot keempat dari grid 2x2. Penjelasannya sebagai berikut:

1. `plt.subplot(2, 2, 4)`: Menentukan subplot keempat dari grid 2x2 untuk menampilkan hasil deteksi warna hijau.

2. `plt.imshow(mask_green, cmap='gray')`: Menampilkan mask warna hijau dalam skala abu-abu menggunakan `imshow()`.

3. `plt.title('Green')`: Menambahkan judul "Green" pada gambar yang ditampilkan di subplot keempat.

4. `plt.xticks(np.arange(0, mask_green.shape[1], 800))` dan `plt.yticks(np.arange(0, mask_green.shape[0], 500))`: Mengatur label sumbu x dan y untuk menampilkan tick mark setiap 800 piksel (x) dan 500 piksel (y) untuk memudahkan dalam mengevaluasi posisi piksel pada gambar.

5. `plt.axis('on')`: Menampilkan sumbu pada gambar.

#menampilkan output
plt.tight_layout()
plt.show()
Baris kode `plt.tight_layout()` digunakan untuk menyesuaikan tata letak subplot secara otomatis sehingga tidak ada tumpang tindih antar subplot.

Kemudian, `plt.show()` digunakan untuk menampilkan semua subplot yang telah disiapkan dalam satu tampilan.


