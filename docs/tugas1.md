# Pendekatan Deret MacLaurin

## Deret MacLaurin

*DERET MacLaurin* adalah Suatu fungsi f(x) yang memiliki turunan *f'(x), f''(x), f'''(x)* dan seterusnya yang kontinyu dalam interval I dengan *a, x I* maka untuk *x* disekitar *a* yaitu *|x-a|<*R , *f(x)* dapat diekspansi kedalam Deret Taylor.

Dalam kasus khusus jika *a=0*, maka disebut *Deret MacLaurin* atau sering disebut Deret Taylor baku. Dan didefinisikan sebagai berikut 

Definisi :
$$
f(x)=f(0)+\frac{f^{1}(0)}{1 !} x+\frac{f^{2}(0)}{2 !} x^{2}+\frac{f^{3}(0)}{3 !} x^{3}+\frac{f^{4}(0)}{4 !} x^{4} + ...+\frac{f^{n}(0)}{n!}x^{n!}
$$


Atau bisa dinyatakan dengan:
$$
f(x)=\sum_{n=0}^\infty \frac{f^{(n)}n(0)}{n!}x^{n}
$$
Deret MacLaurin sangat bermanfaat dalam metode numerik untuk menghitung atau menghampiri nilai-nilai fungsi yang sudah dihitung secara manual seperti nilai *sin x, cos x*, eksponensial, dll. Tentu kita tidak akan bisa menghitung nilai-nilai fungsi tersebut tanpa menggunakan bantuan kalkulator atau tabel. Dalam tulisan ini saya akan mencoba untuk mendekati fungsi-fungsi tersebut menggunakan Deret 
MacLaurin.

## Tugas

Hitunglah e^3x untuk nilai x=4, kemudian expensikan hingga selisih yang dihasilkan kurang dari nilai error yang ditentukan yaitu e < 0,001.

### Penyelesaian

Fungsi awal exponen :
$$
f(x) = e^{3x}\
$$
Dapat juga didefinisikan dengan rumus   : 
$$
e^{3x} = \sum_{n=0}^\infty \frac{(3x)^n}{n!} = \sum_{n=0}^\infty (3)^n\frac{x^n}{n!}
$$
Deret turunan  :
$$
f(a)=e^{3x}
$$
$$
f^{1}(a)=3e^{3x}
$$

$$
f^{2}(a)=9e^{3x}
$$

$$
f^{3}(a)=27e^{3x}
$$

$$
f^{4}(a)=81e^{2x}
$$

$$
...
$$

Berikut adalah penyelesaian untuk mencari nilai expansi :
$$
f(x)=f(0)+\frac{f^{1}(0)}{1 !} x+\frac{f^{2}(0)}{2 !} x^{2}+\frac{f^{3}(0)}{3 !} x^{3}+\frac{f^{4}(0)}{4 !} x^{4} + ...+\frac{f^{n}(0)}{n!}x^{n!}
$$
nilai turunan pada tabel dimasukkan kedalam rumus sehingga didapatkan seperti ini :

$$
f(x)=1+\frac{3}{1 !} x+\frac{9}{2 !} x^{2}+\frac{27}{3 !} x^{3}+\frac{81}{4 !} x^{4} + ...+\frac{3^{n}}{n!} x^{n}
$$
kemudian, nilai x diganti dengan 4 :
$$
f(x)=1+\frac{3}{1 !} 4+\frac{9}{2 !} 4^{2}+\frac{27}{3 !} 4^{3}+\frac{81}{4 !} 4^{4} + ...+\frac{3^{n}}{n!} 4^{n}
$$
perhitungan diatas akan terus berulang hingga nilai selisih mendekati nilai error yang ditentukan yaitu kurang dari 0,001

### Listing Program

**Script**

```python
import math

error = 0.001

def f(x):
    f_turunan = 1
    current=i=0
    iteration = True
    while iteration:
        old= current
        current += (f_turunan*(x**i))/math.factorial(i)
        print('f ke-', i,'=',current, 'Ea=', current-old )
        if current-old < error:
            iteration = False

        else:
            f_turunan *=3
            i +=1

f(4)

```

**Output**

```python
f ke- 0 = 1.0 Ea= 1.0
f ke- 1 = 13.0 Ea= 12.0
f ke- 2 = 85.0 Ea= 72.0
f ke- 3 = 373.0 Ea= 288.0
f ke- 4 = 1237.0 Ea= 864.0
f ke- 5 = 3310.6 Ea= 2073.6
f ke- 6 = 7457.799999999999 Ea= 4147.199999999999
f ke- 7 = 14567.285714285714 Ea= 7109.4857142857145
f ke- 8 = 25231.514285714286 Ea= 10664.228571428572
f ke- 9 = 39450.485714285714 Ea= 14218.971428571429
f ke- 10 = 56513.25142857143 Ea= 17062.765714285713
f ke- 11 = 75127.17766233766 Ea= 18613.926233766237
f ke- 12 = 93741.1038961039 Ea= 18613.926233766237
f ke- 13 = 110923.18965034965 Ea= 17182.085754245752
f ke- 14 = 125650.69172541745 Ea= 14727.502075067794
f ke- 15 = 137432.69338547168 Ea= 11782.00166005423
f ke- 16 = 146269.19463051236 Ea= 8836.50124504068
f ke- 17 = 152506.7249211293 Ea= 6237.530290616938
f ke- 18 = 156665.07844820726 Ea= 4158.3535270779685
f ke- 19 = 159291.4069916249 Ea= 2626.3285434176505
f ke- 20 = 160867.20411767552 Ea= 1575.797126050602
f ke- 21 = 161767.65961827585 Ea= 900.4555006003357
f ke- 22 = 162258.81716405787 Ea= 491.1575457820145
f ke- 23 = 162515.07327490064 Ea= 256.25611084277625
f ke- 24 = 162643.20133032204 Ea= 128.12805542140268
f ke- 25 = 162704.7027969243 Ea= 61.501466602261644
f ke- 26 = 162733.08808920227 Ea= 28.385292277962435
f ke- 27 = 162745.70377465914 Ea= 12.61568545686896
f ke- 28 = 162751.1104969978 Ea= 5.406722338666441
f ke- 29 = 162753.3477614138 Ea= 2.237264416005928
f ke- 30 = 162754.2426671802 Ea= 0.8949057663849089
f ke- 31 = 162754.58908231556 Ea= 0.34641513536917046
f ke- 32 = 162754.71898799133 Ea= 0.12990567577071488
f ke- 33 = 162754.7662264189 Ea= 0.04723842756357044
f ke- 34 = 162754.7828988051 Ea= 0.016672386205755174
f ke- 35 = 162754.7886150518 Ea= 0.005716246698284522
f ke- 36 = 162754.79052046736 Ea= 0.0019054155563935637
f ke- 37 = 162754.79113843996 Ea= 0.0006179726042319089
```



Jadi, proses perulangan akan berhenti pada iterasi ke-37 karena selisih dari expansi yang dihasilkan mendekati nilai error yang ditentukan yaitu e < 0,001.

















































<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$$','$$'],['$','$']]}
});
</script>
  <script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>