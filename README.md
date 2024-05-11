# PCD_UTS_202231091_2024_ITPLN

## IMPORT LIBRARY
```python
import cv2 <br>
```
* Ini mengimpor modul OpenCV, yang memungkinkan Anda untuk menggunakan fungsi dan alat pemrosesan gambar. <br>
```python
import numpy as np
```
* Ini mengimpor modul NumPy, yang sering digunakan untuk manipulasi array numerik, yang akan digunakan untuk manipulasi data gambar. <br>
```python
from matplotlib import pyplot as plt
```
* Ini mengimpor modul pyplot dari pustaka Matplotlib, yang digunakan untuk membuat plot. Ini mungkin akan digunakan untuk menampilkan hasil pemrosesan gambar nanti.

## READ DATA SET
```python
img = cv2.imread("salmanalmuzafar.jpg")
```
* Baris ini mencoba membaca gambar dari file bernama "salmanalmuzafar.jpg" menggunakan fungsi cv2.imread().

## KONVERT BGR TO RGB
```python
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
* Ini berfungsi untuk mengubah format warna gambar dari BGR ke RGB. Mari kita bahas lebih detail:

```python
plt.imshow(rgb)
```
* Menampilkan gambar yang telah dirubah dari BGR menjadi RGB
```python
# Convert to Grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Adjust Contrast dan Brightness
alpha = 1.5  # kontras
beta = 30    # kecerahan
adjusted = cv2.convertScaleAbs(img, alpha=alpha, beta=beta)

# Display Result
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.title('Original Image')
plt.imshow(cv2.cvtColor(img, cv2.CO LOR_BGR2RGB))
plt.axis('off')

plt.subplot(1, 2, 2)
plt.title('Brightened Image')
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.axis('off')

# Menampilkan Gambar
plt.show()
```
* `gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)`: Baris ini mengonversi gambar yang disimpan dalam variabel `img` dari format BGR ke skala keabuan (grayscale) menggunakan fungsi `cv2.cvtColor`. Hasilnya disimpan dalam variabel `gray`.

* `alpha = 1.5` dan `beta = 30`: Ini adalah parameter untuk menyesuaikan kontras dan kecerahan gambar. Nilai `alpha` mengontrol kontras, sedangkan nilai `beta` mengontrol kecerahan. 

* `adjusted = cv2.convertScaleAbs(img, alpha=alpha, beta=beta)`: Baris ini menyesuaikan kontras dan kecerahan gambar menggunakan fungsi `cv2.convertScaleAbs`. Kontras dan kecerahan gambar diatur berdasarkan nilai `alpha` dan `beta`, dan hasilnya disimpan dalam variabel `adjusted`.

* `plt.figure(figsize=(10, 5))`: Baris ini membuat sebuah gambar (figure) dengan ukuran 10x5 inch menggunakan Matplotlib.

* `plt.subplot(1, 2, 1)`: Baris ini menentukan bahwa kita akan menampilkan subplot pertama dari gambar tersebut. Dalam hal ini, kita akan menampilkan gambar asli.

* `plt.title('Original Image')`: Baris ini memberi judul pada subplot pertama sebagai "Original Image".

* `plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))`: Baris ini menampilkan gambar asli dalam subplot pertama. Sebelum menampilkannya, kita harus mengonversi gambar dari format BGR (yang digunakan oleh OpenCV) menjadi format RGB (yang digunakan oleh Matplotlib) menggunakan fungsi `cv2.cvtColor`.

* `plt.axis('off')`: Baris ini menghilangkan sumbu (axis) dari subplot pertama.

* `plt.subplot(1, 2, 2)`: Baris ini menentukan bahwa kita akan menampilkan subplot kedua dari gambar tersebut. Dalam hal ini, kita akan menampilkan gambar yang telah disesuaikan kontras dan kecerahannya.

* `plt.title('Brightened Image')`: Baris ini memberi judul pada subplot kedua sebagai "Brightened Image".

* `plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))`: Baris ini menampilkan gambar yang telah disesuaikan kontras dan kecerahannya dalam subplot kedua. Kembali, kita perlu mengonversi gambar ke format RGB sebelum menampilkannya.

* `plt.axis('off')`: Baris ini menghilangkan sumbu (axis) dari subplot kedua.

* `plt.show()`: Baris ini menampilkan hasil gambar yang telah diproses dan ditampilkan menggunakan Matplotlib.

## DETEKSI RGB
```python
# Display Original Image
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.title('Original Image')

# Display the red channel
plt.subplot(2, 2, 2)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0], cmap="gray")
plt.title('Red Channel')

# Display the green channel
plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1], cmap="gray")
plt.title('Green Channel')

# Display the blue channel
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2], cmap="gray")
plt.title('Blue Channel')

plt.show()
```
* `plt.subplot(2, 2, 1)`: Baris ini menentukan bahwa kita akan menampilkan subplot pertama dari gambar tersebut. Dalam hal ini, kita akan menampilkan gambar asli yang telah disesuaikan kontras dan kecerahannya.

* `plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))`: Baris ini menampilkan gambar asli yang telah disesuaikan kontras dan kecerahannya dalam subplot pertama. Sebelum menampilkannya, kita harus mengonversi gambar dari format BGR (yang digunakan oleh OpenCV) menjadi format RGB (yang digunakan oleh Matplotlib) menggunakan fungsi `cv2.cvtColor`.

* `plt.title('Original Image')`: Baris ini memberi judul pada subplot pertama sebagai "Original Image".

* `plt.subplot(2, 2, 2)`: Baris ini menentukan bahwa kita akan menampilkan subplot kedua dari gambar tersebut. Dalam hal ini, kita akan menampilkan saluran warna merah dari gambar.

* `plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0], cmap="gray")`: Baris ini menampilkan saluran warna merah dari gambar dalam subplot kedua. Kita hanya mengambil saluran merah dengan menggunakan indeks [:,:,0]. `cmap="gray"` digunakan untuk menampilkan gambar dalam skala abu-abu.

* `plt.title('Red Channel')`: Baris ini memberi judul pada subplot kedua sebagai "Red Channel".

* `plt.subplot(2, 2, 3)`: Baris ini menentukan bahwa kita akan menampilkan subplot ketiga dari gambar tersebut. Dalam hal ini, kita akan menampilkan saluran warna hijau dari gambar.

* `plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1], cmap="gray")`: Baris ini menampilkan saluran warna hijau dari gambar dalam subplot ketiga. Kita hanya mengambil saluran hijau dengan menggunakan indeks [:,:,1]. `cmap="gray"` digunakan untuk menampilkan gambar dalam skala abu-abu.

* `plt.title('Green Channel')`: Baris ini memberi judul pada subplot ketiga sebagai "Green Channel".

* `plt.subplot(2, 2, 4)`: Baris ini menentukan bahwa kita akan menampilkan subplot keempat dari gambar tersebut. Dalam hal ini, kita akan menampilkan saluran warna biru dari gambar.

* `plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2], cmap="gray")`: Baris ini menampilkan saluran warna biru dari gambar dalam subplot keempat. Kita hanya mengambil saluran biru dengan menggunakan indeks [:,:,2]. `cmap="gray"` digunakan untuk menampilkan gambar dalam skala abu-abu.

* `plt.title('Blue Channel')`: Baris ini memberi judul pada subplot keempat sebagai "Blue Channel".

* `plt.show()`: Baris ini menampilkan hasil empat subplot yang telah diproses dan ditampilkan menggunakan Matplotlib.

## HISTOGRAM

```python
# Histogram Merah
merah=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0] #Merah
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([merah],[0],None,[256],[0,256])
axs[0].imshow(merah, cmap='gray')
axs[1].plot(hist)
plt.show()
```
Fungsi Kode diatas adalah sebagai berikut:

* `merah=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0]`: Baris ini mengambil saluran warna merah dari gambar yang telah disesuaikan kontras dan kecerahannya, menggunakan indeks [:,:,0]. Ini berarti kita hanya mempertahankan komponen merah dari gambar yang telah diubah ke format RGB.

* `fig, axs = plt.subplots(1,2, figsize = (15,5))`: Baris ini membuat gambar (figure) dan sepasang subplot dalam satu baris, masing-masing dengan ukuran 15x5 inci. Variabel `fig` akan menyimpan referensi ke gambar, sedangkan `axs` akan menjadi array yang berisi referensi ke kedua subplot.

* `hist = cv2.calcHist([merah],[0],None,[256],[0,256])`: Baris ini menghitung histogram dari saluran warna merah yang telah diambil sebelumnya. Fungsi `cv2.calcHist()` digunakan untuk menghitung histogram. Parameter pertama adalah daftar yang berisi gambar yang akan dihitung histogramnya, yang dalam hal ini hanya saluran warna merah. Parameter kedua adalah indeks yang menunjukkan channel yang akan dihitung histogramnya, dalam kasus ini adalah 0 (merah). Parameter ketiga adalah mask, yang di sini diatur sebagai `None`, yang berarti semua piksel dihitung. Parameter keempat adalah jumlah bin histogram, yang diatur sebagai 256. Dan parameter terakhir adalah rentang nilai piksel, yang dalam hal ini adalah 0 hingga 256.

* `axs[0].imshow(merah, cmap='gray')`: Baris ini menampilkan gambar saluran warna merah dalam subplot pertama (`axs[0]`). Karena ini adalah gambar dalam skala abu-abu (grayscale), `cmap='gray'` digunakan untuk menunjukkan bahwa skala warnanya harus disesuaikan dengan skala abu-abu.

* `axs[1].plot(hist)`: Baris ini membuat plot histogram pada subplot kedua (`axs[1]`) menggunakan nilai histogram yang telah dihitung sebelumnya. Plot histogram menunjukkan distribusi intensitas piksel pada saluran warna merah.

* `plt.show()`: Baris ini menampilkan hasil dari kedua subplot yang telah diproses dan ditampilkan menggunakan Matplotlib. Subplot pertama menampilkan gambar saluran warna merah, sedangkan subplot kedua menampilkan histogram dari saluran warna merah tersebut.

```python
#Histogram Hijau
hijau=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1] #hijau
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([hijau],[0],None,[256],[0,256])
axs[0].imshow(hijau, cmap='gray')
axs[1].plot(hist)
plt.show()
```
Kode di atas melakukan hal yang serupa dengan kode sebelumnya, namun kali ini untuk saluran warna hijau dari gambar yang telah disesuaikan kontras dan kecerahannya. Mari kita bahas baris per baris:

* `hijau=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1]`: Baris ini mengambil saluran warna hijau dari gambar yang telah disesuaikan kontras dan kecerahannya, menggunakan indeks [:,:,1]. Ini berarti kita hanya mempertahankan komponen hijau dari gambar yang telah diubah ke format RGB.

* `fig, axs = plt.subplots(1,2, figsize = (15,5))`: Baris ini membuat gambar (figure) dan sepasang subplot dalam satu baris, masing-masing dengan ukuran 15x5 inci. Variabel `fig` akan menyimpan referensi ke gambar, sedangkan `axs` akan menjadi array yang berisi referensi ke kedua subplot.

* `hist = cv2.calcHist([hijau],[0],None,[256],[0,256])`: Baris ini menghitung histogram dari saluran warna hijau yang telah diambil sebelumnya, mirip dengan cara yang dilakukan pada saluran warna merah sebelumnya.

* `axs[0].imshow(hijau, cmap='gray')`: Baris ini menampilkan gambar saluran warna hijau dalam subplot pertama (`axs[0]`). Karena ini adalah gambar dalam skala abu-abu (grayscale), `cmap='gray'` digunakan untuk menunjukkan bahwa skala warnanya harus disesuaikan dengan skala abu-abu.

* `axs[1].plot(hist)`: Baris ini membuat plot histogram pada subplot kedua (`axs[1]`) menggunakan nilai histogram yang telah dihitung sebelumnya. Plot histogram menunjukkan distribusi intensitas piksel pada saluran warna hijau.

* `plt.show()`: Baris ini menampilkan hasil dari kedua subplot yang telah diproses dan ditampilkan menggunakan Matplotlib. Subplot pertama menampilkan gambar saluran warna hijau, sedangkan subplot kedua menampilkan histogram dari saluran warna hijau tersebut.

```python
# Histogram Biru
biru=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2] #biru
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([biru],[0],None,[256],[0,256])
axs[0].imshow(biru, cmap='gray')
axs[1].plot(hist)
plt.show()
```
Kode tersebut melakukan hal yang serupa dengan kode sebelumnya, tetapi kali ini untuk saluran warna biru dari gambar yang telah disesuaikan kontras dan kecerahannya. Mari kita bahas baris per baris:

* `biru=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2]`: Baris ini mengambil saluran warna biru dari gambar yang telah disesuaikan kontras dan kecerahannya, menggunakan indeks [:,:,2]. Ini berarti kita hanya mempertahankan komponen biru dari gambar yang telah diubah ke format RGB.

* `fig, axs = plt.subplots(1,2, figsize = (15,5))`: Baris ini membuat gambar (figure) dan sepasang subplot dalam satu baris, masing-masing dengan ukuran 15x5 inci. Variabel `fig` akan menyimpan referensi ke gambar, sedangkan `axs` akan menjadi array yang berisi referensi ke kedua subplot.

* `hist = cv2.calcHist([biru],[0],None,[256],[0,256])`: Baris ini menghitung histogram dari saluran warna biru yang telah diambil sebelumnya, serupa dengan cara yang dilakukan pada saluran warna merah dan hijau sebelumnya.

* `axs[0].imshow(biru, cmap='gray')`: Baris ini menampilkan gambar saluran warna biru dalam subplot pertama (`axs[0]`). Karena ini adalah gambar dalam skala abu-abu (grayscale), `cmap='gray'` digunakan untuk menunjukkan bahwa skala warnanya harus disesuaikan dengan skala abu-abu.

* `axs[1].plot(hist)`: Baris ini membuat plot histogram pada subplot kedua (`axs[1]`) menggunakan nilai histogram yang telah dihitung sebelumnya. Plot histogram menunjukkan distribusi intensitas piksel pada saluran warna biru.

* `plt.show()`: Baris ini menampilkan hasil dari kedua subplot yang telah diproses dan ditampilkan menggunakan Matplotlib. Subplot pertama menampilkan gambar saluran warna biru, sedangkan subplot kedua menampilkan histogram dari saluran warna biru tersebut.

## AMBANG BATAS CITRA
```python

# Baca gambar
img = cv2.imread('salmanalmuzafar.jpg')
# Convert citra ke grayscale
gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)

# Inisialisasi subplot
fig, axs = plt.subplots(2, 2, figsize=(10,10))

# Ambang batas untuk mendapatkan citra biner (none)
(thresh, binary1) = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')

# Convert citra ke HSV
image_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

# Definisikan range warna biru dalam HSV
blue_lower = np.array([100, 50, 50])
blue_upper = np.array([140, 255, 255])

# Membuat mask untuk warna biru
mask_blue = cv2.inRange(image_hsv, blue_lower, blue_upper)
axs[0,1].imshow(mask_blue, cmap='gray')
axs[0,1].set_title('BLUE')

# Ambang batas untuk mendapatkan citra biner (red-blue)
(thresh, binary3) = cv2.threshold(gray, 43, 255, cv2.THRESH_BINARY)
axs[1,0].imshow(binary3, cmap = 'binary')
axs[1,0].set_title('RED-BLUE')

# Ambang batas untuk mendapatkan citra biner (red-green-blue)
(thresh, binary4) = cv2.threshold(gray, 80, 255, cv2.THRESH_BINARY)
axs[1,1].imshow(binary4, cmap = 'binary')
axs[1,1].set_title('RED-GREEN-BLUE')

plt.show()
```
Kode di atas melakukan beberapa hal terkait pemrosesan gambar untuk mendapatkan nilai ambang batasnya

* Membaca Citra: Citra dengan nama file 'salmanalmuzafar.jpg' dibaca menggunakan fungsi `cv2.imread()`, dan disimpan dalam variabel `img`.

* Konversi ke Grayscale: Citra tersebut kemudian dikonversi ke citra skala abu-abu (grayscale) menggunakan fungsi `cv2.cvtColor()` dengan parameter `cv2.COLOR_RGB2GRAY`. Hasilnya disimpan dalam variabel `gray`.

* Inisialisasi Subplot: Sebuah subplot dengan ukuran 2x2 didefinisikan menggunakan `plt.subplots()`. Ini akan digunakan untuk menampilkan citra-citra hasil pemrosesan.

* Penggunaan Ambang (Thresholding):
   - **THRESH_BINARY**: Dilakukan thresholding pada citra grayscale (`gray`) untuk mendapatkan citra biner (hitam putih) menggunakan `cv2.threshold()`. Hasilnya disimpan dalam `binary1`.
   - **THRESH_BINARY** (dua kali): Dua kali dilakukan thresholding pada citra grayscale (`gray`) dengan nilai ambang yang berbeda untuk mendapatkan citra biner. Hasilnya disimpan dalam `binary3` dan `binary4`.

* Konversi ke HSV dan Segmentasi Warna:
   - Citra awal (`img`) dikonversi ke ruang warna HSV menggunakan `cv2.cvtColor()` dengan parameter `cv2.COLOR_BGR2HSV`. Hasilnya disimpan dalam variabel `image_hsv`.
   - Dilakukan segmentasi warna biru dalam citra HSV menggunakan `cv2.inRange()`, dengan nilai ambang batas yang telah ditentukan (`blue_lower` dan `blue_upper`). Hasilnya disimpan dalam `mask_blue`.

* Menampilkan Citra-Citra Hasil Pemrosesan: Citra-citra hasil pemrosesan ditampilkan dalam subplot yang telah diinisialisasi sebelumnya dengan menggunakan `imshow()`. Setiap subplot diberi judul yang sesuai dengan jenis pemrosesan yang dilakukan.

* Menampilkan Plot: Plot dengan citra-citra hasil pemrosesan ditampilkan menggunakan `plt.show()`.

Dengan demikian, kodingan tersebut melakukan beberapa operasi dasar pada citra, seperti konversi ke grayscale, thresholding untuk mendapatkan citra biner, dan segmentasi warna dalam ruang warna HSV.

## Teori Pendukung
(https://docs.opencv.org/4.x/d7/d4d/tutorial_py_thresholding.html) <br>
(https://youtu.be/ebPiV5M9-DQ?si=VKuk2U0cV0IVHlNz) <br>





