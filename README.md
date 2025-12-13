## 🌌⭐☂️ College-Piechart ☂️⭐🌌
- The pie chart is a favorite chart for many analysts to show the proportion of data. Based on the student dataframe, the number of students per faculty is a case of proportion that can be displayed with a pie chart.
- A pie chart is a type of circular graph, where each "slice" represents a proportion or percentage of the whole data. Its purpose is to show the parts of a total so that the contribution of each category is easily visible.
- In addition, pie charts are often used in business reports, educational research, and public data analysis because of their intuitive and visually appealing shape. However, pie charts are most effective when the number of categories is not too large (usually 4–6 categories) to prevent the visualization from becoming cluttered and difficult to read. With the right color selection, a pie chart can convey information clearly and remain visually pleasing.
- A pie chart is also capable of providing a quick overview without having to read detailed figures, making it suitable for executive presentations or reports that require conveying information concisely yet informatively.
- A pie chart can be supplemented with labels, percentages, or a legend to help the reader understand the value of each category. The use of percentages usually makes interpretation easier because it directly shows the contribution of each part to the total data.
- Showing Proportions and Percentages: A pie chart's core function is to display how different categories contribute to a whole, with each "slice" representing a proportion or percentage of the total data. This makes the contribution of each part easily visible.
- Best for Limited Categories: Pie charts are most effective when the number of categories is small (ideally 4–6). If there are too many slices, the chart becomes cluttered and difficult to read, defeating its purpose of providing a quick, clear overview.
- Visual Communication and Conciseness: Their intuitive circular shape makes them visually appealing and suitable for reports (like executive presentations) where information needs to be conveyed concisely and informatively, often supplemented with labels or a legend for clarity.


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
