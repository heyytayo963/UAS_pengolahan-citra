1. Import Library
```
import numpy as np
import matplotlib.pyplot as plt
import cv2
```
2. Membaca Gambar
```
image = cv2.imread('una.jpg')

if image is None:
    print("Error: Gambar tidak ditemukan atau tidak dapat dimuat.")
```
3. Mengubah Warna Gambar
```
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```
4. Menampilkan Gambar Asli
```
plt.imshow(image)
plt.title('Gambar Asli')
plt.axis('off')
plt.show()
```
5. Menyiapkan Data untuk K-Means
```
pixel_vals = image.reshape((-1, 3))
pixel_vals = np.float32(pixel_vals)
```
6. Parameter K-Means
```
k = 4
criteria = (cv2.TERM_CRITERIA_EPS + cv2.TERM_CRITERIA_MAX_ITER, 100, 0.85)
```
7. Menjalankan K-Means
```
retval, labels, centers = cv2.kmeans(pixel_vals, k, None, criteria, 10, cv2.KMEANS_RANDOM_CENTERS)
```
8. Memproses Output K-Means
```
centers = np.uint8(centers)
segmented_data = centers[labels.flatten()]
segmented_image = segmented_data.reshape((image.shape))
```
9. Menampilkan Gambar Tersegmentasi
```
plt.imshow(segmented_image)
plt.title('Gambar Tersegmentasi dengan Klastering K-Means')
plt.axis('off')
plt.show()
```
