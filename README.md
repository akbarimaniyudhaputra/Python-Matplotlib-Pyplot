
# Python-Matplotlib-Pyplot

## Pie Chart
 - plt.pie()
 
### Untuk lebih jelasnya dapat mengakses laman berikut
 - https://matplotlib.org/3.5.1/api/_as_gen/matplotlib.pyplot.pie.html

#### Perintah untuk mengambil data di file Excel 

```http
import pandas as pd
from pandas import ExcelFile
namaFile = "E:\dataset\smartphone.xlsx"
data = pd.read_excel(namaFile, sheet_name="Sheet1") #sheet_name kalo sheet sj error
data
```

#### Perintah untuk mengambil/menampilkan beberapa kolom/field

```http
#fungsi .filter()
#hanya menampilkan beberapa kolom/field
from pandas import DataFrame
data = data.filter(items=["produsen", "bintang 5"])
data
```

#### Perintah untuk memodifikasi data di kolom/field X

```http
data["bintang 5"] = data["bintang 5"].astype(str) #ubah type data
data["bintang 5"] = [x.replace("rb","00") for x in data["bintang 5"]] #mengubah rb mrnjadi 00
data["bintang 5"] = [x.replace(",","") for x in data["bintang 5"]] #menghilangkan ,
data
```

#### Perintah untuk mengubah tipe data pada semua data di kolom/field X

```http
data["bintang 5"] = data["bintang 5"].astype(int) #ubah type data
data
```

#### Perintah untuk mengurutkan data di kolom/field secara descending (besar ke kecil)

```http
# fungsi .sort_values()
# mengurutkan kolom keuntungan dari besar ke kecil
data.sort_values("bintang 5", axis=0, ascending=False, inplace=True)
data
```

#### Perintah untuk menjadikan data berbentuk list

```http
# fungsi tolist()
# menjadikan data berbentuk list
dataList = data.values.tolist()
dataList
```

#### Perintah untuk merekap/mendaftar banyaknya jumlah X per produk

```http
# membuat sebuah dictionary awal
rekap = {}

for i in range(len(dataList)):
    if dataList[i][0] in rekap: 
        rekap[dataList[i][0]] += dataList[i][1] #menampilkan dataList indeks-0 (kolom/field nama_produk) & indeks-1 (kolom/field bintang 5)
    else:
        rekap[dataList[i][0]] = dataList[i][1] #menampilkan dataList indeks-0 (kolom/field nama_produk) & indeks-1 (kolom/field bintang 5)
rekap
```

#### Perintah untuk membuat pie chart

```http
import matplotlib.pyplot as plt

segmentType = rekap.keys() 
jumlahbentukpersen = rekap.values()

#xiaomi, vivo, samsung, oppo, nan, realme, huawei
explode = (0.1, 0, 0, 0.1, 0.2, 0.3, 0.9) 
color = ("orange", "violet", "blue", "green", "red", "red", "black")

# .figure fungsi untuk mengatur resolusi gambar grafik
#https://matplotlib.org/3.2.1/api/_as_gen/matplotlib.pyplot.figure.html
plt.figure(dpi=180)

# .pie() fungsi untuk membuat diagram lingkaran
# parameter autopct : untuk memberi label pada setiap irisan dengan nilai numeriknya, %1.0f%% artinya menampilkan hasil yang tidak usah angka dibelakang koma
# parameter explode : untuk mengatur jarak setiap irisan 
# parameter colors  : untuk mengatur urutan warna
# parameter pctdistance : untuk mengatur rasio antara bagian tengah setiap irisan chart dan awal teks yang dihasilkan oleh parameter autopct
# parameter startangle  : untuk mengatur sudut di mana awal pie chart diputar, berlawanan arah jarum jam dari sumbu x
# parameter textprops={"fontsize": 8} : untuk mengatur ukuran dari jumlahbentukpersen 
# https://matplotlib.org/3.5.1/api/_as_gen/matplotlib.pyplot.pie.html
plt.pie(jumlahbentukpersen, autopct="%1.0f%%",  explode=explode, colors=color, pctdistance=1.10, startangle=200, textprops={"fontsize": 8})

# .legend() fungsi untuk menampilkan legend 
# parameter loc    : untuk mengatur lokasi/penempatan/posisi legend
# parameter labels : untuk menampilkan label di dalam legend
# https://matplotlib.org/3.5.1/api/_as_gen/matplotlib.pyplot.legend.html
plt.legend(labels=segmentType, loc="best")

# untuk mendifinisikan/mengatur rasio sumbu/bentuk pie chart
plt.axis("equal")

# menyesuaikan posisi/tata letak legend dengan pie chart
# https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.tight_layout.html#matplotlib.pyplot.tight_layout
plt.tight_layout()

# untuk membuat/menambahkan judul 
plt.title("Bintang 5 dari konsumen")

# untuk menampilkan chart
plt.show()
```

## Bar Chart
 - plt.bar()
 - plt.barh() untuk mengubah bentuk ke horizontal
 
### Untuk lebih jelasnya dapat mengakses laman berikut
 - https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.bar.html

#### 1 Perintah untuk mengambil data di file Excel 

```http
import pandas as pd
from pandas import ExcelFile
namaFile = "E:\dataset\smartphone.xlsx"
data = pd.read_excel(namaFile, sheet_name="Sheet1") #sheet_name kalo sheet sj error
data
```

#### 2 Perintah untuk mengambil/menampilkan beberapa kolom/field

```http
#fungsi .filter()
#hanya menampilkan beberapa kolom/field
from pandas import DataFrame
data = data.filter(items=["nama produk", "bintang 5"])
data
```

#### 3 Perintah untuk memodifikasi data di kolom/field X

```http
data["bintang 5"] = data["bintang 5"].astype(str) #ubah type data
data["bintang 5"] = [x.replace("rb","00") for x in data["bintang 5"]] #mengubah rb mrnjadi 00
data["bintang 5"] = [x.replace(",","") for x in data["bintang 5"]] #menghilangkan ,
data
```

#### 4 Perintah untuk mengubah tipe data pada semua data di kolom/field X

```http
data["bintang 5"] = data["bintang 5"].astype(int) #ubah type data
data
```

#### 5 Perintah untuk mengurutkan data di kolom/field secara descending (besar ke kecil)

```http
# fungsi .sort_values()
# mengurutkan kolom keuntungan dari besar ke kecil
data.sort_values("bintang 5", axis=0, ascending=False, inplace=True)
data
```

#### 6 #### Perintah untuk menjadikan data berbentuk list

```http
# fungsi tolist()
# menjadikan data berbentuk list
dataList = data.values.tolist()
dataList
```

#### 7 Perintah untuk melakukan rekap/mendafatar jumlah X per produk dalam bentuk dictionary

```http
# membuat sebuah dictionary awal
rekap = {}

for i in range(len(dataList)):
    if dataList[i][0] in rekap: 
        rekap[dataList[i][0]] += dataList[i][1] #menampilkan dataList indeks-0 (kolom/field nama_produk) & indeks-1 (kolom/field bintang 5)
    else:
        rekap[dataList[i][0]] = dataList[i][1] #menampilkan dataList indeks-0 (kolom/field nama_produk) & indeks-1 (kolom/field bintang 5)
rekap
```

#### 8  Perintah untuk melakukan sorting data & mengambil kunci (keys) elemen di dalam dictionary 

```http
#fungsi .sort() untuk melakukan sorting data 
#fungsi .keys() untuk mengambil kunci (keys) elemen di dalam dictionary https://kelasprogrammer.com/8-fungsi-dictionary-di-python/
#nama produk (sebagai key/kunci) diubah ke dalam bentuk list 
#tersimpan dalam bentuk data list

namaproduk = list(rekap.keys())
namaproduk.sort()
namaproduk
```

#### 9 Perintah untuk melakukan penyusunan pada indeks ke-1 (jumlah bintang 5) di dataList sesuai dengan posisi/urutan di variabel namaproduk

```http
#melakukan penyusunan pada indeks ke-1 (jumlah bintang 5) di dataList sesuai dengan posisi/urutan di variabel namaproduk
#disimpan dalam bentuk data list
# fungsi .append() untuk menambahkan/memasukkan data/item dimulai dari belakang https://www.petanikode.com/python-list/

jumlahbintang5 = []
for jb5 in namaproduk:
    jumlahbintang5.append(rekap[jb5])
jumlahbintang5
```

#### 10 Perintah untuk melakukan sorting data pada variabel jumlahbintang5 (kecil ke besar)

```http
#fungsi .sort() untuk melakukan sorting data 

jumlahbintang5.sort()
jumlahbintang5
```

#### 11 Perintah untuk membuat bar chart

```http
import matplotlib.pyplot as plt
import numpy as np

# .figure fungsi untuk mengatur resolusi gambar grafik
#https://matplotlib.org/3.2.1/api/_as_gen/matplotlib.pyplot.figure.html
plt.figure(figsize=(10, 9.5), dpi=180)

# .bar() fungsi untuk membuat diagram batang
plt.bar(namaproduk, jumlahbintang5, width=0.5, color="red")

# untuk membuat/menambahkan judul 
plt.title("Bintang 5 dari konsumen")

# untuk membuat/menambahkan label pada garis Y 
plt.ylabel("jumlah bintang 5")
# untuk membuat/menambahkan label pada garis X
plt.xlabel("nama produk")

# mengambil variabel namaproduk & mengatur lokasi/posisi/tata letak pada label sumbu x. https://matplotlib.org/3.5.1/api/_as_gen/matplotlib.pyplot.xticks.html
plt.xticks(namaproduk, fontsize=5, rotation=90)
#plt.yticks(jumlahbintang5, fontsize=5)

# untuk menambahkan garis bantu 
#plt.grid(True)  #https://handhikayp.medium.com/membuat-grafik-chart-dari-suatu-data-menggunakan-python-7a0337645f96
plt.grid(color='darkgray', linestyle=':', linewidth=0.5) #https://medium.com/sysinfo/data-visualization-with-python-matplotlib-for-beginner-part-1-6b6d74025a24

# enumerate(jumlahbintang5) fungsi untuk mengembalikan nilai variabel jumlahbintang5 secara iterasi/perulangan dengan/beserta indeksnya
for indexnya, nilainya in enumerate(jumlahbintang5):
    plt.annotate("{:,}".format(nilainya) , xy=(indexnya, nilainya +50), fontstyle="italic", ha="center" ,va="bottom", fontsize=5, rotation=90)
    
# menyesuaikan posisi/tata letak agar tidak ada bagian yg kepotong saat ditampilkan di format .png
plt.tight_layout()
    
# untuk menampilkan chart
plt.savefig("Vertikalnew.png", format="png")
plt.show()
plt.close()
```

#### 12 Perintah untuk mengubah bar chart ke barh chart (dalam bentuk horizontal)

```http
import matplotlib.pyplot as plt
import numpy as np

# .figure fungsi untuk mengatur resolusi gambar grafik
#https://matplotlib.org/3.2.1/api/_as_gen/matplotlib.pyplot.figure.html
plt.figure(dpi=250)

# .barh() fungsi untuk mengubah posisi diagaram batang menjadi horizontal 
plt.barh(namaproduk, jumlahbintang5, color="green")

# untuk membuat/menambahkan judul 
plt.title("Bintang 5 dari konsumen")

# untuk membuat/menambahkan label pada garis Y 
plt.ylabel("nama produk")
# untuk membuat/menambahkan label pada garis X
plt.xlabel("jumlah bintang 5")


# mengambil variabel namaproduk & mengatur lokasi/posisi/tata letak pada label sumbu y. https://matplotlib.org/3.5.1/api/_as_gen/matplotlib.pyplot.xticks.html
plt.yticks(namaproduk, fontsize=3)

# untuk menambahkan garis bantu 
#plt.grid(True)  #https://handhikayp.medium.com/membuat-grafik-chart-dari-suatu-data-menggunakan-python-7a0337645f96
plt.grid(color='darkgray', linestyle=':', linewidth=0.5)

# enumerate(jumlahbintang5) fungsi untuk mengembalikan nilai variabel jumlahbintang5 secara iterasi/perulangan dengan/beserta indeksnya
for indexnya, nilainya in enumerate(jumlahbintang5):
    plt.annotate("{:,}".format(nilainya) , xy=(nilainya +50, indexnya), fontstyle="italic", va="center", fontsize=4)

plt.tight_layout()
    
# untuk menampilkan chart
plt.savefig("Horizontalnew.png", format="png")
plt.show()
plt.close()
```
