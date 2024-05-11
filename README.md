
# PCD_UTS_202231051_2024_ITPLN
## Pengolahan citra 
  Citra digital adalah sebuah fungsi 2D, f(x,y), yang merupakan fungsi intensitas
cahaya, dimana nilai x dan y merupakan koordinat spasial dan nilai fungsi di setiap titik
(x,y) merupakan tingkat keabuan citra pada titik tersebut. Citra digital dinyatakan dengan
sebuah matriks dimana baris dan kolomnya menyatakan suatu titik pada citra tersebut dan
elemen matriksnya (yang disebut sebagai elemen gambar atau piksel) menyatakan tingkat
keabuan pada titik tersebut. Matriks dari citra digital berukuran NxM (tinggi x lebar),
dimana:

N = jumlah baris 0 < y ≤ N – 1
M = jumlah kolom 0 ≤ x ≤ M – 1
L = derajat keabuan 0 ≤ f(x,y) ≤ L – 1

Dimana indeks baris (x) dan indeks kolom (y) menyatakan suatu koordinat titik pada
citra, sedangkan f(x,y) merupakan intensitas (derajat keabuan) pada titik (x,y).
Berdasarkan jenisnya, citra digital dapat dibagi menjadi 3 (Sutoyo, 2009), yaitu:

**1. Citra Biner (Monokrom)**
Memiliki 2 buah warna, yaitu hitam dan putih. Warna hitam bernilai 1 dan warna
putih bernilai 0. Untuk menyimpan kedua warna ini dibutuhkan 1 bit di memori.
Tahapan penyelesaian produk

**2. Citra Grayscale (skala keabuan)**
Citra grayscale mempunyai kemungkinan warna hitam untuk nilai minimal dan
warna putih untuk nilai maksimal. Banyaknya warna tergantung pada jumlah bit yang
disediakan di memori untuk menampung kebutuhan warna tersebut.
Semakin besar jumlah bit warna yang disediakan di memori, maka semakin halus
gradasi warna yang terbentuk.

**3.Citra Warna (true color)**
Setiap piksel pada citra warna mewakili warna yang merupakan kombinasi tiga warna
dasar, yaitu merah, hijau, dan biru (RGB = Red, Green, Blue). Setiap warna dasar
menggunakan penyimpanan 8 bit = 1 byte (nilai maksimum 255 warna), jadi satu piksel
pada citra warna diwakili oleh 3 byte.
Pengolahan citra digital adalah salah satu bentuk pemrosesan informasi dengan
inputan berupa citra (image) dan keluaran yang juga berupa citra atau dapat juga bagian
dari citra tersebut. Tujuan dari pemrosesan ini adalah memperbaiki kualitas citra agar
mudah diinterpretasi oleh manusia atau mesin komputer

## Konversi BGR dan RGB dengan Python, OpenCV (cvtColor)
Konversi antara BGR (Blue, Green, Red) dan RGB (Red, Green, Blue) adalah konversi antara dua model warna yang umum digunakan dalam pemrosesan citra digital.

1. **BGR (Blue, Green, Red)**:
   - Ini adalah model warna yang umum digunakan dalam OpenCV, sebuah perpustakaan populer untuk pengolahan citra dan komputer vision.
   - Urutan warna dalam BGR adalah biru, hijau, dan merah.
   - Dalam BGR, warna biru disimpan di saluran pertama, hijau di saluran kedua, dan merah di saluran ketiga.

2. **RGB (Red, Green, Blue)**:
   - Ini adalah model warna yang paling umum digunakan di dunia digital, termasuk dalam tampilan monitor, kamera digital, dan banyak lagi.
   - Urutan warna dalam RGB adalah merah, hijau, dan biru.
   - Dalam RGB, warna merah disimpan di saluran pertama, hijau di saluran kedua, dan biru di saluran ketiga.

Konversi antara BGR dan RGB melibatkan menukar posisi saluran warna. Ini perlu dilakukan ketika Anda bekerja dengan gambar menggunakan berbagai perangkat lunak atau alat yang menggunakan model warna yang berbeda. Misalnya, jika Anda ingin memproses gambar menggunakan OpenCV (yang menggunakan BGR), tetapi ingin menampilkannya di browser web atau program lain yang mengharapkan format RGB, Anda perlu melakukan konversi antara BGR dan RGB. Biasanya, algoritma yang sederhana, seperti menukar saluran atau menggunakan fungsi bawaan dari library yang Anda gunakan, dapat melakukan konversi tersebut dengan mudah.
Ambang batas (thresholding) adalah teknik pemrosesan citra yang digunakan untuk memisahkan piksel-piksel dalam citra menjadi dua kelas berdasarkan intensitasnya. Tujuan utamanya adalah untuk mengubah citra menjadi citra biner di mana piksel-pikselnya hanya memiliki nilai 0 (hitam) atau 255 (putih), tergantung pada apakah nilai intensitasnya melebihi atau kurang dari suatu ambang tertentu.

### Prinsip Thresholding:
1. **Pengukuran Intensitas**: Pertama-tama, ambang batas memerlukan pengukuran intensitas piksel dalam citra. Intensitas ini sering kali dinyatakan dalam skala abu-abu, di mana nilai-nilai lebih tinggi menunjukkan kecerahan yang lebih besar.

2. **Pemilihan Ambang**: Ambang batas memerlukan ambang yang dipilih sebelumnya. Ambang ini merupakan nilai tertentu yang digunakan untuk membedakan antara piksel yang dianggap sebagai bagian dari objek (misalnya, benda yang diinginkan untuk dikenali dalam citra) dan latar belakang (bagian lain dari citra yang tidak dianggap sebagai objek).

3. **Konversi Menjadi Citra Biner**: Setelah ambang dipilih, citra asli diperiksa piksel demi piksel. Jika intensitas piksel melebihi ambang, piksel tersebut diubah menjadi nilai 255 (putih); jika tidak, nilainya diubah menjadi 0 (hitam). Dengan demikian, kita mendapatkan citra biner di mana hanya ada dua nilai intensitas yang mungkin.

### Jenis-jenis Thresholding:
1. **Thresholding Global**: Dalam metode ini, satu ambang diterapkan pada seluruh citra. Ini adalah pendekatan yang paling sederhana tetapi mungkin tidak efektif jika citra memiliki variasi intensitas yang signifikan.

2. **Thresholding Adaptif**: Metode ini menggunakan ambang yang berbeda-beda untuk setiap bagian citra. Ini lebih efektif untuk citra yang memiliki variasi intensitas yang signifikan.

3. **Thresholding Otsu**: Metode ini secara otomatis menentukan ambang terbaik berdasarkan analisis histogram citra. Ini adalah metode yang baik jika ambang yang optimal tidak diketahui.
### Implementasi:
Di berbagai perpustakaan pemrosesan citra, seperti OpenCV (dalam bahasa pemrograman Python), terdapat fungsi-fungsi yang memudahkan implementasi thresholding. Anda dapat mengatur ambang secara manual atau menggunakan metode otomatis seperti Otsu. Kemudian, hasilnya dapat digunakan untuk tujuan tertentu, seperti segmentasi objek atau deteksi fitur.

# Tahapan Tahapan 
1. **IMPORT LIBRARY**
 ``` python
   import cv2
import numpy as np
from matplotlib import pyplot as plt
 ```
1. `import cv2`: Ini seperti meminta Python untuk membawa koper yang berisi alat untuk bekerja dengan gambar dan video. Jadi, jika kita butuh membaca gambar, memprosesnya, atau melakukan hal-hal lain dengan gambar, kita punya alat yang tepat.
2. `import numpy as np`: Ini seperti meminta Python untuk membawa kotak dengan alat matematika yang canggih. Jadi, jika kita butuh melakukan operasi matematika seperti penjumlahan, perkalian, atau yang lebih kompleks pada data kita, kita bisa menggunakan alat ini.
3. `from matplotlib import pyplot as plt`: Ini seperti meminta Python untuk membawa pensil dan kertas yang bagus untuk membuat grafik dan plot. Jadi, jika kita ingin menunjukkan data kita dalam bentuk grafik atau plot, kita punya pensil dan kertas yang tepat untuk melakukannya.

2. **MEMBACA GAMBAR**
   ``` python
   img = cv2.imread("nama.jpeg")
 ```
kede di atas berfungsi untuk membaca gambar yang kita mau
3. **KONVERT BGR KE RGB**
 ``` python
  rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
 ```
img adalah gambar yang ingin kita ubah skemanya.
cv2.COLOR_BGR2RGB adalah kode yang memberitahu OpenCV bahwa kita ingin mengonversi dari skema warna BGR ke skema warna RGB.
 ``` python
  plt.imshow(rgb)
 ```
Ini adalah perintah untuk menampilkan gambar dalam format RGB.
4. **ADJUSTED IMAGE AND SHARPENED IMAGE**
 ``` python
 alpha = 1
beta = 30    
adjusted = cv2.convertScaleAbs(img, alpha=alpha, beta=beta)

kernel_sharpening = np.array([[-1,-1,-1], [-1,9,-1], [-1,-1,-1]])
sharpened = cv2.filter2D(adjusted, -1, kernel_sharpening)

plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.title('Original Image')
plt.imshow(rgb)
plt.axis('off')

plt.subplot(1, 3, 2)
plt.title('Adjusted Image')
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.axis('off')

plt.subplot(1, 3, 3)
plt.title('Sharpened Image')
plt.imshow(cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB))
plt.axis('off')

plt.show()
 ```
1. **Penyesuaian Kontras dan Kecerahan**:
   - `cv2.convertScaleAbs()` digunakan untuk menyesuaikan kontras dan kecerahan gambar.
   - `alpha` adalah faktor kontras dan `beta` adalah faktor kecerahan.
   - `adjusted` adalah gambar hasil penyesuaian kontras dan kecerahan.

2. **Pengasaman Citra**:
   - `cv2.filter2D()` digunakan untuk menerapkan filter pada gambar.
   - `kernel_sharpening` adalah kernel yang digunakan untuk meningkatkan ketajaman gambar.
   - `sharpened` adalah gambar hasil dari pengasaman citra.

3. **Tampilan Gambar**:
   - `plt.subplot()` digunakan untuk membuat tata letak plot multi-gambar.
   - Setiap subplot menampilkan gambar dengan judul yang sesuai.
   - `plt.imshow()` digunakan untuk menampilkan gambar dalam plot.
   - `plt.axis('off')` menghilangkan sumbu x dan y pada plot.

4. **Menampilkan Plot**:
   - `plt.show()` menampilkan plot yang telah dibuat.

Dengan menggunakan kode ini, kita dapat melihat visualisasi dari langkah-langkah pemrosesan citra yang dilakukan, mulai dari gambar asli, gambar yang disesuaikan kontras dan kecerahannya, hingga gambar yang telah diperbaiki dengan meningkatkan ketajaman.
5. **DETEKSI RGB
``` python
  plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.title('Original Image')

plt.subplot(2, 2, 2)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0], cmap="gray")
plt.title('Red Channel')

plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1], cmap="gray")
plt.title('Green Channel')

plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2], cmap="gray")
plt.title('Blue Channel')

plt.show()
 ```
Kode tersebut membagi gambar yang telah disesuaikan (adjusted) menjadi tiga saluran warna: merah, hijau, dan biru, dan menampilkannya dalam plot yang berbeda. Berikut adalah penjelasan lebih rinci:

1. **Original Image**:
   - Pada subplot pertama (`plt.subplot(2, 2, 1)`), gambar asli yang telah disesuaikan ditampilkan.
   - `plt.imshow()` digunakan untuk menampilkan gambar dalam plot.
   - `plt.title()` memberikan judul untuk subplot ini, yang dalam hal ini adalah "Original Image".

2. **Red Channel (Saluran Merah)**:
   - Pada subplot kedua (`plt.subplot(2, 2, 2)`), hanya saluran warna merah dari gambar yang ditampilkan.
   - `cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0]` digunakan untuk memilih saluran merah dari gambar yang telah disesuaikan.
   - `cmap="gray"` digunakan untuk menampilkan citra dalam skala abu-abu (grayscale).

3. **Green Channel (Saluran Hijau)**:
   - Pada subplot ketiga (`plt.subplot(2, 2, 3)`), hanya saluran warna hijau dari gambar yang ditampilkan.
   - `cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1]` digunakan untuk memilih saluran hijau dari gambar yang telah disesuaikan.

4. **Blue Channel (Saluran Biru)**:
   - Pada subplot keempat (`plt.subplot(2, 2, 4)`), hanya saluran warna biru dari gambar yang ditampilkan.
   - `cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2]` digunakan untuk memilih saluran biru dari gambar yang telah disesuaikan.
8. **AMBANG BATAS**
``` python
image_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)

fig, axs = plt.subplots(2, 2, figsize=(10,10))

red_lower1 = np.array([0, 50, 50])
red_upper1 = np.array([10, 255, 255])
red_lower2 = np.array([170, 50, 50]) 
red_upper2 = np.array([180, 255, 255])

green_lower = np.array([36, 50, 50])
green_upper = np.array([86, 255, 255])

blue_lower = np.array([100, 50, 50])
blue_upper = np.array([140, 255, 255])

mask_red1 = cv2.inRange(image_hsv, red_lower1, red_upper1)
mask_red2 = cv2.inRange(image_hsv, red_lower2, red_upper2)
mask_red = cv2.bitwise_or(mask_red1, mask_red2)  # Combine the red masks
mask_green = cv2.inRange(image_hsv, green_lower, green_upper)
mask_blue = cv2.inRange(image_hsv, blue_lower, blue_upper)

combined_mask1 = np.bitwise_or(mask_red, mask_blue)
combined_mask2 = np.bitwise_or(combined_mask1, mask_green)

(thresh, binary1) = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')

plt.figure(figsize=(12, 10))
plt.subplot(1, 3, 1)
axs[0,1].imshow(mask_blue, cmap='gray')
axs[0,1].set_title('Blue Mask')
plt.axis('off')

plt.subplot(1, 3, 2)
axs[1,0].imshow(combined_mask1, cmap='gray')
axs[1,0].set_title('Red-Blue Mask')
plt.axis('off')

plt.subplot(1, 3, 3)
axs[1,1].imshow(combined_mask2, cmap='gray')
axs[1,1].set_title('Red-Green-Blue Mask')
plt.axis('off')

plt.show()
```
Kode ini melakukan segmentasi warna pada gambar menggunakan model warna HSV (Hue, Saturation, Value) dan menghasilkan beberapa masker warna yang berbeda. Berikut adalah penjelasan singkatnya:

1. **Konversi ke Model Warna HSV dan Grayscale**:
   - `cv2.cvtColor()` digunakan untuk mengonversi gambar dari skema warna BGR ke HSV dan RGB ke grayscale.
   - Ini memungkinkan kita untuk bekerja dengan gambar dalam skema warna yang lebih sesuai untuk deteksi warna (HSV) dan analisis intensitas (grayscale).

2. **Pengaturan Rentang Warna untuk Setiap Warna Utama**:
   - Rentang warna yang sesuai untuk warna merah, hijau, dan biru ditentukan dalam format HSV.
   - Ini dilakukan dengan menentukan batas bawah dan atas untuk setiap saluran warna (hue, saturation, value).

3. **Pembuatan Masker Warna**:
   - `cv2.inRange()` digunakan untuk membuat masker untuk setiap warna utama berdasarkan rentang warna yang telah ditentukan.
   - Setiap masker memisahkan area dengan warna tertentu dari gambar asli.

4. **Gabungan Masker**:
   - Masker untuk warna merah dan biru digabungkan menggunakan operasi bitwise OR, menghasilkan masker gabungan yang mencakup kedua warna.
   - Masker untuk warna hijau ditambahkan ke masker gabungan dengan operasi bitwise OR, menghasilkan masker gabungan untuk semua warna utama.

5. **Pembuatan Binary Image dari Grayscale**:
   - `cv2.threshold()` digunakan untuk membuat citra biner dari gambar grayscale.
   - Ini menghasilkan gambar biner di mana piksel dengan intensitas di atas ambang batas akan diubah menjadi putih, sementara yang di bawahnya menjadi hitam.

6. **Tampilan Hasil Segmentasi**:
   - Hasil segmentasi untuk setiap warna dan kombinasi warna ditampilkan dalam subplot menggunakan `imshow()`.
   - Setiap subplot diberi judul sesuai dengan warna atau kombinasi warna yang di-segmentasi.
