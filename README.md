## 🌌⭐☂️ College-Piechart ☂️⭐🌌
- Pie chart merupakan chart favorit bagi banyak analis untuk menunjukkan proporsi data. Berdasarkan data frame mahasiswa, jumlah mahasiswa per fakultas adalah kasus proporsi yang dapat ditampilkan dengan pie chart.

## 🌌⭐☂️ Code ☂️⭐🌌
- Terlampir code sebagai berikut:
```
library(ggplot2)
library(openxlsx)
#Membaca file mahasiswa.xlsx
mahasiswa <- read.xlsx("https://storage.googleapis.com/dqlab-dataset/mahasiswa.xlsx",sheet = "Sheet 1")

#Menghitung Jumlah Data by Fakultas
summarybyfakultas <- aggregate(x=mahasiswa$JUMLAH, by=list(Kategori=mahasiswa$Fakultas), FUN=sum)
summarybyfakultas <- setNames(summarybyfakultas, c("fakultas","jumlah_mahasiswa"))

piechart<- ggplot(summarybyfakultas, aes(x="", y=jumlah_mahasiswa, fill=fakultas))+ geom_bar(width = 1, stat = "identity")
piechart <- piechart + coord_polar("y", start=0)
piechart <- piechart + ggtitle("Disribusi Mahasiswa per Fakultas")
piechart <- piechart + scale_fill_brewer(palette="Blues")+ theme_minimal()
piechart <- piechart + guides(fill=guide_legend(title="Fakultas"))
piechart <- piechart + ylab("Jumlah Mahasiswa") 
piechart
```

## 🌌⭐☂️ Result ☂️⭐🌌
- Terlihat bahwa porsi fakultas "Seni dan Desain" dan "Ilmu Komunikasi" menempati porsi terbesar. Angka 0 s/d 5000 yang ditampilkan di luar pie chart menunjukkan rentang jumlah mahasiswa secara akumulatif.
  
![image](https://github.com/diantyapitaloka/College-Piechart/assets/147487436/03c33c1c-f0b5-4166-8d89-f381dc739881)

- Selanjutnya, kita akan melihat untuk fakultas Bisnis yang menempati porsi pie chart pada angka 0 dan di bawah 1000 (ditunjukkan dengan anak panah merah).

![image](https://github.com/diantyapitaloka/College-Piechart/assets/147487436/7c26d313-7a33-412c-bf4d-d307313250bc)

- Hal ini konsisten dengan informasi dari grafik histogram sebelumnya, bahwa jumlah mahasiswa fakultas Bisnis memang berada di bawah angka 1000.
![image](https://github.com/diantyapitaloka/College-Piechart/assets/147487436/225335f7-6e85-4dc0-a7f6-c70cbcd5d45a)

- Jika kita tambahkan jumlah mahasiswa fakultas "Bisnis", "D3 Perhotelan", dan "ICT" maka jumlahnya tidak akan mencapai 2000 mahasiswa, seperti yang telah tergambarkan pada pie chart ini.


## 🌌⭐☂️ Copyright ☂️⭐🌌
By Diantya Pitaloka
