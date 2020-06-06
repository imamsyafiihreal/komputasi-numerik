# **Metode dan Simulasi Monte Carlo**[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#metode-dan-simulasi-monte-carlo)

#### Metode Monte Carlo[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#metode-monte-carlo)

> Metode *Monte Carlo* adalah [algoritma ](http://id.wikipedia.org/wiki/Algoritma)[kom*put*asi ](http://id.wikipedia.org/wiki/Komputasi)untuk [mensimulasikan](http://id.wikipedia.org/wiki/Simulasi) berbagai perilaku sistem fisika dan matematika. Penggunaan klasik metode ini adalah untuk mengevaluasi [integral definit, ](http://id.wikipedia.org/w/index.php?title=Integral_definit&action=edit&redlink=1)terutama integral multidimensi dengan syarat dan batasan yang rumit
>
> Melihat dari cara kerjanya metode *Monte Carlo* merupakan metode yang memberikan segala kemungkinan nilai dari suatu variabel. Metode *Monte Carlo* merupakan metode yang memanfaatkan *strong law of large number* dalam melakukan perhitungan, artinya semakin banyak variabel acak yang digunakan akan semakin baik pula pendekatan nilai eksaknya

#### Algoritma dan contoh metode monte carlo[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#algoritma-dan-contoh-metode-monte-carlo)

1. Probabilitas pelemparan coin Ganda

Dari teori peluang akan muncul:

MM Î ¼ MB atau BM Î ½ BB Î ¼

Dengan metode Monte Carlo dapatkan tingkat ketelitian sampai 0.01 untuk menyelesaikan kasus tersebut….

Untuk mendapatkan ketelitian sampai 0,01 maka harus dilakukan pelemparan sebanyak 1000 (N_total) kali. Dari hasil pelemparan catat keluarnya angka-angka:

P(MM) = N(MM)/N_total

P(MB) = N(MB)/N_total

P(BB) = N(BB)/N_total

##### ALGORITHMA[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#algorithma)

a. Bangkitkan nilai 0/1 sebanyak 1000 kali (N=1000) dengan cara: n1 =(int)rand()%2 dan n2 =(int)rand()%2

b. Klasifikasi Jika n1=0 dan n2=0, maka MM=MM+1 Jika n1=0 dan n2=1 atau n1=1 dan n2=0 maka MB=MB+1 Jika n1=1 dan n2=1, maka BB=BB+1

c. Hitung probabilitas MM dengan cara N(MM)/N dan probabilitas untuk nilai MB serta BB

2.Menghitung Nilai Integral dengan monte carlo

![img](https://riyanhidayat0811.github.io/Tugas/1.jfif)

Luas area dicari = yang berwarna atau daerah dibawah garis fungsi f(x) = 2x

Dengan dasar pemikiran tersebut diperoleh suatu perbandingan:

![img](https://riyanhidayat0811.github.io/Tugas/2.jfif)

BIla kita melakukan pelemparan coin sebanyak N kali, dan coin jatuh di bawah garis f(x) =2x sebanyak M kali. Maka:

![img](https://riyanhidayat0811.github.io/Tugas/4.jfif)

## *tugas programing*[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#tugas-programing)

![img](https://riyanhidayat0811.github.io/Tugas/3.jfif)

#### implemenasi metode carlo dalam python[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#implemenasi-metode-carlo-dalam-python)

```
from scipy import random
import numpy as np
import matplotlib.pyplot as plt

a = 0
b = 2
N=2500


def func(x):
    return (4-x**2)**0.5


area = []
for i in range(N):
    xrand = np.zeros(N)

    for i in range(len(xrand)):
        xrand[i] = random.uniform(a,b)
        integral = 0.0

    for i in range(N):
        integral+=func(xrand[i])

    jawab = (b-a)/float(N)*integral
    area.append(jawab)

plt.title("Hasil phi")
plt.hist(area,bins = 30, ec = 'black')
plt.xlabel("Area")
plt.show()
```

#### *hasil running*[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#hasil-running)

![img](https://riyanhidayat0811.github.io/Tugas/hsl.jfif)

```
from scipy import random
import numpy as np

a = -1
b = 1
N=100
xrand=np.zeros(N)
yrand=np.zeros(N)
zrand=np.zeros(N)
integral=0.0
for i in range(4):
    for i in range(len(xrand)):
        xrand[i]=random.uniform(a,b)

    for i in range(len(yrand)):
        yrand[i]=random.uniform(a,b)

    for i in range(len(zrand)):
        zrand[i]=random.uniform(a,b)

    def func(x,y,z):
        return (x**2)+(y**2)+(z**2)


    for i in range(N):
        integral+=func(xrand[i],yrand[i],zrand[i])

jawab=(b-a)/float(N)*integral
print("jawab: ",jawab)
```

#### *hasil running*[¶](https://riyanhidayat0811.github.io/Tugas/Monte Carlo/#hasil-running_1)

```
jawab:  7.941487167529855
```