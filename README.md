## 🌌⭐☂️ College-Piechart ☂️⭐🌌
- The pie chart is a favorite chart for many analysts to show the proportion of data. Based on the student dataframe, the number of students per faculty is a case of proportion that can be displayed with a pie chart.
- A pie chart is a type of circular graph, where each "slice" represents a proportion or percentage of the whole data. Its purpose is to show the parts of a total so that the contribution of each category is easily visible.
- In addition, pie charts are often used in business reports, educational research, and public data analysis because of their intuitive and visually appealing shape. However, pie charts are most effective when the number of categories is not too large (usually 4–6 categories) to prevent the visualization from becoming cluttered and difficult to read. With the right color selection, a pie chart can convey information clearly and remain visually pleasing.
- Highlighting Dominant Categories: A pie chart excels at instantly identifying the "lion's share" within a dataset. For instance, if the Faculty of Engineering holds 50% of the total student body, the semi-circle shape provides an immediate visual cue of that dominance.
- Contextualizing with "Other" Groupings: When dealing with many small faculties, grouping them into an "Other" category keeps the visualization clean. This ensures the 4–6 category rule is maintained while still accounting for 100% of the student population.
- A pie chart is also capable of providing a quick overview without having to read detailed figures, making it suitable for executive presentations or reports that require conveying information concisely yet informatively.
- A pie chart can be supplemented with labels, percentages, or a legend to help the reader understand the value of each category. The use of percentages usually makes interpretation easier because it directly shows the contribution of each part to the total data.
- The Power of Data Sorting: Sorting slices from largest to smallest, starting at the 12 o'clock position, significantly improves readability. This logical progression allows the eye to follow the decrease in faculty size in a predictable, clockwise motion.
- Comparing Subgroups via Nested Pies: While standard pies show one level of data, a "Sunburst" or nested pie chart can show sub-faculties within a larger college. This allows you to visualize both the main faculty and its specific departments in one cohesive circular flow.
- Minimalist Design for High Impact: Removing unnecessary borders or 3D effects keeps the focus on the actual area of the slices. A flat, 2D design is often preferred in modern academic reporting to avoid the optical illusions that 3D tilting can create.
- Effective Use of "Exploded" Slices: You can pull a specific slice away from the center of the chart to draw the reader's eye to a particular faculty. This "exploded" effect is perfect for highlighting a new department or one that requires urgent administrative attention.
- Color Theory for Categorization: Using distinct, high-contrast colors for each faculty prevents the slices from blending together. A well-chosen palette ensures that even without reading labels, viewers can distinguish between different academic fields.
- Showing Proportions and Percentages: A pie chart's core function is to display how different categories contribute to a whole, with each "slice" representing a proportion or percentage of the total data. This makes the contribution of each part easily visible.
- Best for Limited Categories: Pie charts are most effective when the number of categories is small (ideally 4–6). If there are too many slices, the chart becomes cluttered and difficult to read, defeating its purpose of providing a quick, clear overview.
- Visual Communication and Conciseness: Their intuitive circular shape makes them visually appealing and suitable for reports (like executive presentations) where information needs to be conveyed concisely and informatively, often supplemented with labels or a legend for clarity.
- Demonstrates Proportions of a Whole: The fundamental role of a pie chart is to visualize the parts of a total. Each slice represents a clear proportion or percentage of the entire dataset, making the contribution of each category immediately visible.
- Optimal for Limited Categories: They are most effective when the dataset has a small number of categories (ideally 4–6). Using a pie chart with too many categories can lead to a cluttered and difficult-to-interpret visualization.
- Facilitates Quick, Concise Communication: Pie charts are highly valued in business and reports because their intuitive shape allows for a quick overview without needing detailed figures. They are perfect for executive summaries or reports that require conveying information concisely yet informatively.
- Strategic Starting Point: To enhance readability, the largest slice should typically begin at the 12 o’clock position and progress clockwise. This follows natural eye-tracking patterns and helps the audience immediately identify the most significant category.
- The Power of Contrast: High-contrast color palettes should be used to differentiate between adjacent slices, especially when categories have similar values. This ensures that the boundaries of each "piece of the pie" are distinct and prevents the data from blending together visually.
- Labeling for Accessibility: Instead of relying solely on a separate legend, try placing data labels and percentages directly onto or next to the corresponding slices. This reduces the "eye-darting" effect, allowing the viewer to process the category and its value simultaneously without searching for a key.
- Avoiding 3D Distortions: While 3D pie charts might look modern, they often distort the actual proportions of the data by making the slices in the "front" appear larger than they are. Stick to 2D designs to maintain mathematical accuracy and ensure the viewer perceives the true relationship between the parts.
- The "Other" Category Strategy: If you have many small categories that would clutter the chart, group them into a single "Other" slice to maintain a clean visual. This keeps the focus on the primary faculties or departments while still accounting for 100% of the student population.
- Logical Ordering of Data: Aside from the largest slice, the remaining categories should generally be ordered by size from largest to smallest. This hierarchical structure makes it much easier for a stakeholder to compare the relative importance of different groups at a glance.
- Contextualizing with Titles: Every pie chart should be accompanied by a descriptive title that explains exactly what the "whole" represents, such as "Total Student Enrollment by Faculty 2026." Clear titling prevents ambiguity and ensures the proportion shown is grounded in a specific context.
- The Donut Chart Alternative: If you find the pie chart feels a bit too "heavy," consider using a donut chart by removing the center of the circle. This design offers a more modern aesthetic and provides a central space where you can display the total aggregate number for the entire dataset.
- Mindful Use of Whitespace: Incorporating thin white borders between slices can significantly improve the clarity of the chart, especially when using a similar color gradient. This small design choice prevents the sections from bleeding into one another, making the proportional breakdown look professional and sharp.


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
