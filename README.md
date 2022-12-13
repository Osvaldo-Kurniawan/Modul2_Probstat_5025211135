# Modul2_Probstat_5025211135
Repository untuk pengerjaan Praktikum 2 mata kuliah Probabilitas dan Statistik 2022.

</br>

## Identitas
#### Nama    : Gabrielle Immanuel Osvaldo Kurniawan
#### NRP     : 5025211135
#### Kelas   : Probabilitas dan Statistik A

</br>

## Soal 1
Seorang peneliti melakukan penelitian mengenai pengaruh aktivitas 𝐴 terhadap kadar saturasi oksigen pada manusia. Peneliti tersebut mengambil sampel sebanyak 9 responden. Pertama, sebelum melakukan aktivitas 𝐴, peneliti mencatat kadar saturasi oksigen dari 9 responden tersebut. Kemudian, 9 responden tersebut diminta melakukan aktivitas 𝐴. Setelah 15 menit, peneliti tersebut mencatat kembali kadar saturasi oksigen dari 9 responden tersebut. Berikut data dari 9 responden mengenai kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas 𝐴.

| Responden   | X        | Y        |
|-------------|----------|----------|
| 1 | 78 | 100 |
| 2 | 75 | 95 |
| 3 | 67 | 70 |
| 4 | 77 | 90 |
| 5 | 70 | 90 |
| 6 | 72 | 90 |
| 7 | 78 | 89 |
| 8 | 74 | 90 |
| 9 | 77 | 100 |

Berdasarkan data pada tabel diatas, diketahui kadar saturasi oksigen dari responden ke-3 ketika belum melakukan aktivitas 𝐴 sebanyak 67, dan setelah melakukan aktivitas 𝐴 sebanyak 70.

### Poin A
> Carilah standar deviasi dari data selisih pasangan pengamatan tabel di atas.

Hitung selisih dari antar data ( before and after ) pada setiap subyek penelitian. Kemudian, hitung mean dari selisih-selisih tersebut.
```R
difference <- after - before
difference
mean(difference)
sd(difference)
```
Hasil : </br>
![image.png]( https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/1.a.png )

</br>

### Poin B
>Carilah nilai t (p-value).

Solusi uji berpasangan dilakukan dengan menggunakan fungsi `t.test()` sebagai berikut :

```R
t.test(after, before, paired = TRUE)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/1.b.png)

</br>

### Poin C
>Tentukanlah apakah terdapat pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan aktivitas 𝐴 jika diketahui tingkat signifikansi 𝛼 = 5% serta H0 : “tidak ada pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan aktivitas 𝐴”

Dari uji 𝑡 (p-value) didapat hasil 6.003e-05 atau 0.00006003 (0.05>0.00006003), maka terima h1. 

</br>

## Soal 2
Diketahui bahwa mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun. Untuk menguji klaim ini, 100 pemilik mobil yang dipilih secara acak diminta untuk mencatat jarak yang mereka tempuh. Jika sampel acak menunjukkan rata-rata 23.500 kilometer dan standar deviasi 3900 kilometer. (Kerjakan menggunakan 2 library seperti referensi pada modul).
### Poin A
>Apakah Anda setuju dengan klaim tersebut?

Setuju, karena dengan rata-rata 23.5000 dari sampel acak dengan standar deviasi 3900 kilometer, maka nilai klaim tersebut mendekati atau  valid. Dimana data bisa mengikuti sebaran normal.

</br>

### Poin B
>Jelaskan maksud dari output yang dihasilkan!

Fungsi yang digunakan adalah fungsi `tsum.test()` . Fungsi tersebut ada pada library BSDA sehingga harus diinstall dulu.

```R
install.packages("BSDA")
library(BSDA)
tsum.test(mean.x = 23500, s.x = 3900, n.x = 100)
```

Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/2.png)

Hal tersebut berarti dengan interval kepercayaan 95%, rata-rata jarak tempuh mobil per tahun berada di antara 22.726,16 km dan 24.273,84 km. 

Dengan interval kepercayaan 95% dan dari 100 responden, dapat dibuktikan bahwa rata-rata jarak tempuh mobil per thn lebih dari 20.000 km karena nilai p-value kurang dari tingkat signifikansi 𝛼 = 0.05.

</br>

### Poin C
>Buatlah kesimpulan berdasarkan P-Value yang dihasilkan!

Terima h1, pada populasi tertentu sebuah mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun.

</br>

## Soal 3
Diketahui perusahaan memiliki seorang data analyst ingin memecahkan permasalahan pengambilan keputusan dalam perusahaan tersebut. Selanjutnya didapatkanlah data berikut dari perusahaan saham tersebut.

| Nama Kota/Atribut   | Bandung        | Bali       |
|-------------|----------|----------|
| Jumlah Saham              | 19 | 27 |
| Sampel Mean               | 3.64 | 2.79 |
| Sampel Standar Deviasi    | 1.67 | 1.32 |

Dari data diatas berilah keputusan serta kesimpulan yang didapatkan dari hasil diatas. Asumsikan nilai variancenya sama, apakah ada perbedaan pada rata-ratanya (α= 0.05)? Buatlah:

### Poin A
>H0 dan H1

Berdasarkan deskripsi dan data yang terlampir, maka dapat disusun hipotesis H0 dan H1 sebagai berikut.
- h0← μ1 = μ2 (rata-rata saham di Bandung sama dengan di Bali)
-h1← μ1 ≠ μ2 (rata-rata saham di Bandung tidak sama dengan di Bali)

</br>

### Poin B
>Hitung sampel statistik

Solusi dilakukan dengan menggunakan fungsi `tsum.test()`. Fungsi tersebut menghasilkan nilai dari sampel statistik.

```R
tsum.test(mean.x=3.64, s.x = 1.67, n.x = 19, 
          mean.y =2.79 , s.y = 1.32, n.y = 27, 
          alternative = "greater", var.equal = TRUE)
```

Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/3.b.png)

</br>

### Poin C
>Lakukan uji statistik (df =2)

Digunakan fungsi `plotDist()` pada library Mosaic untuk mendapatkan gambaran atau visualisasi dari statistik dengan derajat bebas sebesar 2.

```R
install.packages("mosaic")
library(mosaic)
plotDist(dist = 't', df = 2, col = "red")
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/3.c.png)

</br>

### Poin D
>Nilai Kritikal

Digunakan fungsi `qchisq()` dengan nilai `df` sesuai dengan yang telah terlampir untuk mendapatkan nilai kritikal.

```R
qchisq(p = 0.05, df = 2, lower.tail = FALSE)
```

Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/3.d.png)

</br>

### Poin E
>Keputusan

Terima h0.

</br>

### Poin F
>Kesimpulan

jika dilihat dari uji statistik didapatkan perbedaan rata-rata yang terjadi tidak ada .

</br>

## Soal 4
Seorang Peneliti sedang meneliti spesies dari kucing di ITS. Dalam penelitiannya ia mengumpulkan data tiga spesies kucing yaitu kucing oren, kucing hitam dan kucing putih dengan panjangnya masing-masing.

Jika diketahui dataset pada **https://intip.in/datasetprobstat1** dan H0 adalah tidak ada perbedaan panjang antara ketiga spesies atau rata-rata panjangnya sama, maka kerjakan atau carilah:

### Poin A
>Buatlah masing masing jenis spesies menjadi 3 subjek "Grup" (grup 1, grup 2, dan grup 3). Lalu gambarkan plot kuantil normal untuk setiap kelompok dan lihat apakah ada outlier utama dalam homogenitas varians.

*Pertama*, memasukkan data dari dataset yang disediakan.

```R
dataoneway = read.table(file = "C:\\Users\\OSVALDO KURNIAWAN\\OneDrive\\ITS\\Mata Kuliah\\Semester 3\\Probabilistik Statistika\\Praktikum 2\\data_soal_4.txt", header = TRUE)
attach(dataoneway)
names(dataoneway)
```

*Kedua*, melakukan grouping sesuai dengan label yang telah ditentukan sekaligus melakukan pengecekan value dalam grup yang dihasilkan.

```R
dataoneway$Group <- as.factor(dataoneway$Group)
dataoneway$Group = factor(dataoneway$Group, labels = c("Kucing Oren", "Kucing Hitam", "Kucing Putih"))

class(dataoneway$Group)
```

*Ketiga*, membagi tiap valuer menjadi 3 bagian sesuai dengan label grup yang telah dibuat.

```R
Group1 <- subset(dataoneway, Group == "Kucing Oren")
Group2 <- subset(dataoneway, Group == "Kucing Hitam")
Group3 <- subset(dataoneway, Group == "Kucing Putih")
```

*Keempat*, menggambar plot kuantil normal untuk setiap grup untuk melihat distribusi data dan outlier utama dalam homogenitas varians pada masing-masing grup.

```R
qqnorm(Group1$Length)
qqline(Group1$Length)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/4.a.1.png)

```R
qqnorm(Group2$Length)
qqline(Group2$Length)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/4.a.2.png)

```R
qqnorm(Group3$Length)
qqline(Group3$Length)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/4.a.3.png)

</br>

### Poin B
>Carilah atau periksalah homogeneity of variances-nya. Berapa nilai p yang didapatkan? Apa hipotesis dan kesimpulan yang dapat diambil?

Untuk mendapatkan homogeneity of variances, digunakan sebuah fungsi yaitu fungsi `bartlett.test()` dengan parameter dari data yang telah dimasukkan sebelumnya.

```R
bartlett.test(Length ~ Group, data = dataoneway)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/4.b.png)

Dari hasil uji fungsi `bartlett.test()` didapatkan p-value sebesar 0.8054 yang lebih dari nilai 𝛼 = 0.05 sehingga asumsi kesamaan varians terpenuhi.

</br>

### Poin C
>Untuk uji ANOVA (satu arah), buatlah model linier dengan panjang versus grup dan beri nama model tersebut model 1.

Untuk membuat uji anova dan model liniernya, digunakan fungsi yaitu fungsi `lm()` dan `anova()` dengan parameter dari data yang telah dimasukkan sebelumnya.

```R
model1 = lm(Length ~ Group, data = dataoneway)
anova(model1)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/4.c.png)

</br>

### Poin D
>Dari hasil poin C, berapakah nilai p? Apa yang dapat Anda simpulkan dari H0?

Berdasarkan hasil yang didapatkan pada poin sebelumnya, pada taraf uji 5% didapatkan nilai p-value sebesar 0.0013. Maka, terdapat perbedaan panjang kucing yang signifikan berdasarkan grupnya.

</br>

### Poin E
>Verifikasilah jawaban model 1 dengan Post-hoc test Tukey HSD, dari nilai p yang didapatkan apakah satu jenis kucing lebih panjang dari yang lain? Jelaskan.

Untuk verifikasi jawaban model 1 sebelumnya, digunakan sebuah fungsi yaitu fungsi `TukeyHSD()` dengan parameter model 1 dari AOV sebelumnya.

```R
TukeyHSD(aov(model1))
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/4.e.png)

Dari hasil uji Tukey, dapat dilihat kombinasi dari kelompok mana yang secara signifikan berbeda. Jika menggunakan 𝛼 = 5%, **perbedaan panjang kucing yang signifikan adalah grup 2 (Kucing Hitam) terhadap grup 1 (Kucing Oren) dan grup 3 (Kucing Putih)**.

</br>

### Poin F
>Visualisasikan data dengan ggplot2

Digunakan fungsi `ggplot()` untuk melakukan visualisasi data.

```R
install.packages("ggplot2")
library("ggplot2")
ggplot(dataoneway, aes(x = Group, y = Length)) + geom_boxplot(fill = "grey80", colour = "black") + scale_x_discrete() + xlab("Treatment Group") + ylab("Length (cm)")
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/4.f.png)

</br>

## Soal 5
Data yang digunakan merupakan hasil eksperimen yang dilakukan untuk mengetahui pengaruh suhu operasi (100˚C, 125˚C, dan 150˚C) dan tiga jenis kaca pelat muka (A, B dan C) pada keluaran cahaya tabung osiloskop. Percobaan dilakukan sebanyak 27 kali dan didapatkan [**data hasil eksperimen berikut**](https://drive.google.com/file/d/1aLUOdw_LVJq6VQrQEkuQhZ8FW43FemTJ/view). Dengan data tersebut:

### Poin A
>Buatlah plot sederhana untuk visualisasi data

*Pertama*, Install library.

```R
install.packages("multcompView")
library(readr)
library(ggplot2)
library(multcompView)
library(dplyr)
```

*Kedua*, memasukkan dan membaca dataset yang telah disediakan.

```R
GTL <- read_csv("C:\\Users\\OSVALDO KURNIAWAN\\OneDrive\\ITS\\Mata Kuliah\\Semester 3\\Probabilistik Statistika\\Praktikum 2\\data_soal_5.csv")
head(GTL)
```

*Ketiga*, melakukan observasi pada dataset.

```R
str(GTL)
```

*Keempat*, melakukan viasualisasi dengan menggunakan simple plot dengan fungsi `qplot()` sebagai berikut.

```R
qplot(x = Temp, y = Light, geom = "point", data = GTL) + facet_grid(.~Glass, labeller = label_both)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/5.a.png)

</br>

### Poin B
>Lakukan uji ANOVA dua arah

*Pertama*, membuat variabel as factor sebagai ANOVA.

```R
GTL$Glass <- as.factor(GTL$Glass)
GTL$Temp_Factor <- as.factor(GTL$Temp)
str(GTL)
```

*Kedua*, melakukan analisis of variance (AoV) dengan fungsi `summary(aov())` sebagai berikut.

```R
anova <- aov(Light ~ Glass*Temp_Factor, data = GTL)
summary(anova)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/5.b.png)

</br>

### Poin C
>Tampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi)

Sebagai solusinya, digunakan fungsi `group_by()` yang selanjutnya digunakan untuk melakukan data summary dengan fungsi `summarise()` sesuai mean dan standar deviasi yang berlaku sebagai berikut.

```R
data_summary <- group_by(GTL, Glass, Temp) %>%
  summarise(mean = mean(Light), sd = sd(Light)) %>%
  arrange(desc(mean))
print(data_summary)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/5.c.png)

</br>

### Poin D
>Lakukan uji Tukey

Pengujian Tukey menggunakan fungsi `TukeyHSD()` sebagai berikut:

```R
tukey <- TukeyHSD(anova)
print(tukey)
```
Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/5.d.1.png)
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/5.d.2.png)

</br>

### Poin E
>Gunakan compact letter display untuk menunjukkan perbedaan signifikan antara uji Anova dan uji Tukey

*Pertama*, membuat compact letter display dengan fungsi `multcompLetterS4()` sebagai berikut.

```R
tukey.cld <- multcompLetters4(anova, tukey)
print(tukey.cld)
```

*Kedua*, menambahkan compact letter display tersebut ke tabel dengan mean dan standar deviasi yang telah dibuat sebelumnya.

```R
cld <- as.data.frame.list(tukey.cld$`Glass:Temp_Factor`)
data_summary$Tukey <- cld$Letters
print(data_summary)
```

Hasil : </br>
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/5.e.png)
![image.png](https://github.com/Osvaldo-Kurniawan/Modul2_Probstat_5025211135/blob/main/Screenshot/5.f.png)
