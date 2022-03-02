
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
