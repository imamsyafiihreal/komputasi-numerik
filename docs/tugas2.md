# Numerical Solution of Algebraic and Transcendental Equation

## 1. Mencari akar dengan cara Bisection

Metode bisection adalah algoritma pencarian akar pada sebuah interval. Interval tersebut membagi dua bagian lalu memilih bagian mana yang mengandung akar dan bagian yang tidak mengandung akar dibuang. Hal ini dilakukan berulang-ulang hingga diperoleh akar persamaan atau mendekati akar persamaan. Metode ini berlaku ketika ingin memecahkan persamaan ![f(x)=0](https://s0.wp.com/latex.php?latex=f%28x%29%3D0&bg=ffffff&fg=666666&s=0) dengan ![f(x)](https://s0.wp.com/latex.php?latex=f%28x%29&bg=ffffff&fg=666666&s=0) merupakan fungsi kontinyu.

```python
def bisection(f,a,b,N):

    if f(a)*f(b) >= 0:
        print("Bisection method fails.")
        return None
    a_n = a
    b_n = b
    for n in range(1,N+1):
        m_n = (a_n + b_n)/2
        f_m_n = f(m_n)
        if f(a_n)*f_m_n < 0:
            a_n = a_n
            b_n = m_n
        elif f(b_n)*f_m_n < 0:
            a_n = m_n
            b_n = b_n
        elif f_m_n == 0:
            print("Found exact solution.")
            return m_n
        else:
            print("Bisection method fails.")
            return None
    return (a_n + b_n)/2
f = lambda x: x**2 - 5*x + 6
approx_phi = bisection(f,1,2.3,25)
print(approx_phi)
```

output

```python
1.9999999985098835
```

## 2. Mencari akar dengan cara Newton-Rapshon

Metode Newton-Raphson adalah metode pencarian akar suatu fungsi ![f(x)](https://s0.wp.com/latex.php?latex=f%28x%29&bg=ffffff&fg=666666&s=0) dengan pendekatan satu titik, dimana fungsi ![f(x](https://s0.wp.com/latex.php?latex=f%28x&bg=ffffff&fg=666666&s=0) mempunyai turunan. Metode ini dianggap lebih mudah dari [**Metode Bagi-Dua**](https://aimprof08.wordpress.com/2012/08/30/metode-bagi-dua-bisection-method/) (Bisection Method) karena metode ini menggunakan pendekatan satu titik sebagai titik awal, semakin dekat titik awal yang kita pilih dengan akar sebenarnya maka semakin cepat konvergen ke akarnya.

```
def newton(f,Df,x0,epsilon,max_iter):

    xn = x0
    for n in range(0,max_iter):
        fxn = f(xn)
        if abs(fxn) < epsilon:
            print('Found solution after',n,'iterations.')
            return xn
        Dfxn = Df(xn)
        if Dfxn == 0:
            print('Zero derivative. No solution found.')
            return None
        xn = xn - fxn/Dfxn
    print('Exceeded maximum iterations. No solution found.')
    return None
p = lambda x: x**2 - 5*x + 6
Dp = lambda x: 2*x - 5 
approx = newton(p,Dp,1,1e-3,10)
print(approx)
```

output

```
Found solution after 4 iterations.
1.9999847409781035
```

## 3. Mencari akar dengan cara Secant

Pada Metode Newton-Raphson memerlukan syarat wajib yaitu fungsi ![f(x)](https://s0.wp.com/latex.php?latex=f%28x%29&bg=ffffff&fg=666666&s=0) harus memiliki turunan ![f'(x)](https://s0.wp.com/latex.php?latex=f%27%28x%29&bg=ffffff&fg=666666&s=0)., sehingga syarat wajib ini dianggap sulit karena tidak semua fungsi bisa dengan mudah mencari turunannya. Oleh karena itu, muncul ide dari yaitu mencari persamaan yang ekivalen dengan rumus turunan fungsi. Ide ini lebih dikenal dengan nama Metode Secant. Ide dari metode ini yaitu menggunakan gradien garis yang melalui titik ![(x_0, f(x_0))](https://s0.wp.com/latex.php?latex=%28x_0%2C+f%28x_0%29%29&bg=ffffff&fg=666666&s=0) dan ![(x_1, f(x_1))](https://s0.wp.com/latex.php?latex=%28x_1%2C+f%28x_1%29%29&bg=ffffff&fg=666666&s=0). 

```python
def secant(f,a,b,N):


    if f(a)*f(b) >= 0:
        print("Secant method fails.")
        return None
    a_n = a
    b_n = b
    for n in range(1,N+1):
        m_n = a_n - f(a_n)*(b_n - a_n)/(f(b_n) - f(a_n))
        f_m_n = f(m_n)
        if f(a_n)*f_m_n < 0:
            a_n = a_n
            b_n = m_n
        elif f(b_n)*f_m_n < 0:
            a_n = m_n
            b_n = b_n
        elif f_m_n == 0:
            print("Found exact solution.")
            return m_n
        else:
            print("Secant method fails.")
            return None
    return a_n - f(a_n)*(b_n - a_n)/(f(b_n) - f(a_n))

p = lambda x: x**2 - 5*x + 6
approx = secant(p,1,2.4,20)
print(approx)
```

output

```pyth
2.0000003178913373
```

## 4. Mencari akar dengan cara Regulasi Falsi

Metode Regular Falsi adalah panduan konsep [**Metode Bagi-Dua**](https://aimprof08.wordpress.com/2012/08/30/metode-bagi-dua-bisection-method/) dan [**Metode Secant**](https://aimprof08.wordpress.com/2012/09/01/metode-secant-secant-method/) dimana menggunakan konsep [**Metode Bagi-Dua**](https://aimprof08.wordpress.com/2012/08/30/metode-bagi-dua-bisection-method/) karena dimulai dengan pemilihan dua titik awal ![x_0](https://s0.wp.com/latex.php?latex=x_0&bg=ffffff&fg=666666&s=0) dan ![x_1](https://s0.wp.com/latex.php?latex=x_1&bg=ffffff&fg=666666&s=0) sedemikian sehingga ![f(x_0)](https://s0.wp.com/latex.php?latex=f%28x_0%29&bg=ffffff&fg=666666&s=0) dan ![f(x_1)](https://s0.wp.com/latex.php?latex=f%28x_1%29&bg=ffffff&fg=666666&s=0) berlawanan tanda atau ![f(x_0) f(x_1) < 0](https://s0.wp.com/latex.php?latex=f%28x_0%29+f%28x_1%29+%3C+0&bg=ffffff&fg=666666&s=0). Kemudian menggunakan konsep [**Metode Secant**](https://aimprof08.wordpress.com/2012/09/01/metode-secant-secant-method/) yaitu dengan menarik garis ![l](https://s0.wp.com/latex.php?latex=l&bg=ffffff&fg=666666&s=0) dari titik ![f(x_0)](https://s0.wp.com/latex.php?latex=f%28x_0%29&bg=ffffff&fg=666666&s=0) dan ![f(x_1)](https://s0.wp.com/latex.php?latex=f%28x_1%29&bg=ffffff&fg=666666&s=0) sedemikian sehingga garis ![l](https://s0.wp.com/latex.php?latex=l&bg=ffffff&fg=666666&s=0) berpotongan pada sumbu – ![x](https://s0.wp.com/latex.php?latex=x&bg=ffffff&fg=666666&s=0) dan memotong kurva atau grafik fungsi pada titik ![f(x_0)](https://s0.wp.com/latex.php?latex=f%28x_0%29&bg=ffffff&fg=666666&s=0) dan ![f(x_1)](https://s0.wp.com/latex.php?latex=f%28x_1%29&bg=ffffff&fg=666666&s=0). Sehingga **Metode Regular Falsi** ini akan menghasilkan titik potong pada sumbu-![x](https://s0.wp.com/latex.php?latex=x&bg=ffffff&fg=666666&s=0) yaitu ![x_2](https://s0.wp.com/latex.php?latex=x_2&bg=ffffff&fg=666666&s=0) yang merupakan calon akar dan tetap berada dalam interval ![[x_0, x_1]](https://s0.wp.com/latex.php?latex=%5Bx_0%2C+x_1%5D&bg=ffffff&fg=666666&s=0). Metode ini kemudian berlanjut dengan menghasilkan berturut-turut interval ![[x_{n-1}, x_n]](https://s0.wp.com/latex.php?latex=%5Bx_%7Bn-1%7D%2C+x_n%5D&bg=ffffff&fg=666666&s=0) yang semuanya berisi akar ![f](https://s0.wp.com/latex.php?latex=f&bg=ffffff&fg=666666&s=0).

```python
error = 0.01
a = 0
b = 2.1

def f(x):
    return x**2 - 5*x + 6

def regulasi_falsi(a,b):
    i=0
    max_iter = 50
    iteration = True
    while iteration and i < max_iter:
        if f(a)*f(b) < 0:
            x = (a*abs(f(b)) + b*abs(f(a))) / (abs(f(a)) + abs(f(b)))
            if f(a)*f(x) < 0:
                b = x

            if f(x)*f(b) < 0:
                a = x

            if abs(a-b) < error:
                iteration = False
            else:
                i+=1
        else:
            print('tidak di temukan akar')
    print('x =', x)


regulasi_falsi(a,b)
```

output

```python
x = 2.000000000174259
```

