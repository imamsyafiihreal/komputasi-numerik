# *Methode Euler*

​	Dalam [matematika](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Mathematics&usg=ALkJrhjDWC7mFYv9qZjq7EpYkcEL9stHPA) dan [ilmu komputasi](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Computational_science&usg=ALkJrhhMvXEENQGAcZ8rfwcBV1ty27UwVg) , **metode Euler** (juga disebut **metode forward Euler** ) adalah prosedur [numerik](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Numerical_analysis&usg=ALkJrhiHNA08sVwe_pQQoM47EMj_WihQUw) orde pertama untuk menyelesaikan [persamaan diferensial biasa](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Ordinary_differential_equation&usg=ALkJrhj5IdtWdujDH-_1GB2stUS1e1jHQw) (ODE) dengan [nilai awal yang](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Initial_value_problem&usg=ALkJrhhMCcGHiTFoHZ-fNHkePEgI-kBdsQ) diberikan. Ini adalah [metode eksplisit](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Explicit_and_implicit_methods&usg=ALkJrhgMyCOq0YQEYnoWkMzViVyiGMLwIA) paling dasar untuk [integrasi numerik persamaan diferensial biasa](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Numerical_ordinary_differential_equations&usg=ALkJrhhSiv-erFNcLX_saKOf2cHK4Shl4w) dan merupakan [metode Runge-Kutta](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Runge%E2%80%93Kutta_method&usg=ALkJrhhwIzjYIcv_nVtmKWsBcjP7a4mMbA) paling sederhana. Metode Euler dinamai [Leonhard Euler](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Leonhard_Euler&usg=ALkJrhjB04743Oiy6h6I7qfgSNgAYSz2PQ) , yang memperlakukannya dalam bukunya *[Institutionum calculi integralis](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Institutionum_calculi_integralis&usg=ALkJrhh1Tc89QNZTcWuB1Co8divPc4WEgg)* (diterbitkan 1768-1870). [[1\]](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Euler_method&usg=ALkJrhhvr5EDmqbzf3GyrdrsZEj2XNIOcw#cite_note-1)

​	Metode Euler adalah metode urutan pertama, yang berarti bahwa kesalahan lokal (kesalahan per langkah) sebanding dengan kuadrat ukuran langkah, dan kesalahan global (kesalahan pada waktu tertentu) sebanding dengan ukuran langkah. Metode Euler sering berfungsi sebagai dasar untuk membangun metode yang lebih kompleks, misalnya, metode [prediktor-korektor](https://translate.googleusercontent.com/translate_c?client=srp&depth=1&hl=id&rurl=translate.google.com&sl=en&sp=nmt4&tl=id&u=https://en.m.wikipedia.org/wiki/Predictor%E2%80%93corrector_method&usg=ALkJrhiJ-Z8eEH6Wlelmm5peOsKLX4f0Vw) .



# *Contoh soal*

Buatlah program untuk menyelesaikan persamaan differensial biasa berikut dengan menggunakan metode Euler

![](soal.png)



Untuk menentukan y(1.01), y(1.02) dan y(1.03).



##### Code Program dengan Python

```python
print("f(x,y)=1+x^2")
print("yi+1 = y1 + hf(xi+yi)")
x1 = float(input("Masukkan x1= "))
x2 = float(input("Masukkan x2= "))

h = 1.01-x1 #Langsung saya atur sendiri karena yang dicari f(x,y) nilai x-nya=1.01
n=4 #jumlah x ada 4 yaitu 1, 1.01, 1.02, 1.03
xi = -4
hasil = xi
y=0
for i in range(n):
    print("hasil dari y"+str(i)+"= "+ str(hasil))
    hasil = xi + h*(1+(x1+y)**2)
    y+=h
    xi=hasil
```



pada bagian pertama terdapat variable x1 adalah x awal dan x2 merupakan x akhir. karena di soal terdapat nx=3 yaitu x0=1, x1=1,01, x3=1,02 x2=1,03 maka h= xn-x0/n, hasilnya h = 0.01.

xi adalah hasil awal yang kemudian akan dimasukkan pada prosess iterasi. Karena rumus eurel adalah y1 = y0 +h(f(x,y)) maka rumus barunya adalah y1=y0+h(1+x^2). variable y digunakan untuk penambahan nilai x agar selalu bertambah 0.01.











```html
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$$','$$'],['$','$']]}
});
</script>
  <script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
```

