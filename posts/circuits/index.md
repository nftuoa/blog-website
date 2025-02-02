---
title: "《Fundamentals of Electric Circuits》(Alexander)习题解答 "
author: "Oscar Tuo"
date: "2025-01-27"
categories: [circuit]

---

我该管管自己这个酷爱开新坑的毛病了（

## 第一章

### 1.1 
a.
$$ Q=ne=-0.1036 C$$
b.
$$ Q=ne=-0.1986 C$$
c.
$$ Q=ne=-3.947 C$$
d.
$$ Q=ne=-26.081 C$$

### 1.2
a.
$$ i=\frac{dq}{dt}=3 mA$$

b.
$$ i=\frac{dq}{dt}=(16t+4) A$$

c.
$$ i=\frac{dq}{dt}=(-3e^{-t}+10e^{-2t}) nA$$

d.
$$ i=\frac{dq}{dt}=1200{\pi}cos(120{\pi}t)  pA$$

e.
$$ i=\frac{dq}{dt}=(-80e^{-4t}cos(50t)-20e^{-4t}sin(50t)) {\mu}A$$

### 1.3

a.
$$q(t)=q(0)+\int i(t)=(1+3t) C $$
b.
$$q(t)=q(0)+\int i(t)=(t^2+5t) C$$
c.
$$q(t)=q(0)+\int i(t)=(20sin(10t+\pi/6)+2)\mu C$$
d.
$$ q(t)=q(0)+\int i(t)=\frac{(-30(sin(40t)-40cos(40t))e^{-30t}}{250}C$$


### 1.4
$$Q=\int_{t0}^{t}i dt=\int_{0s}^{20s}idt=148C$$

### 1.5
$$Q=\int_{t0}^{t}idt=\int_{0s}^{10s}\frac{t}{2}=25C$$

### 1.6

$$Q=\begin{cases}15tmC,& 0ms\le t \le 2ms,\\30mC,&2ms<t<8ms,\\(90-7.5t)mC,&8ms\le t \le 12ms \end{cases}$$

then, 
$$i=\frac{dQ}{dt}=\begin{cases}15A,&0ms\le t \le 2ms, \\ 0,&2ms<t<8ms,\\ -7.5A,&8ms\le t \le 12ms,\end{cases}  $$

then $$ i\arrowvert _{t=1ms}=15A,i\arrowvert _{t=6ms}=0,i\arrowvert _{t=10ms}=-7.5A,$$

### 1.7
$$i=\begin{cases}25A,& 0\le t \le 2s,\\-25A,&2s<t<6s,\\25A,&6s\le t \le 8s \end{cases}$$

### 1.8
$$i=\begin{cases}10tmA,& 0\le t \le 1ms,\\10mA,&1ms<t<2ms,\end{cases}$$
$$Q=\int_{t0}^{t}i=\int_{0}^{1ms}i+\int_{1ms}^{2ms}i=5\mu C+10\mu C=15\mu C$$

### 1.9
$$i=\begin{cases}10A,& 0\le t \le 1s,\\(15-5t)A,&1s<t<2s,\\5A,&2s\le t \le 4s,\\(25-5t),&4s<t\le5s \end{cases}$$
then,
$$ Q=\int_{t0}^{t}i=\begin{cases}10t C,& 0\le t \le 1s,\\(15t-2.5t^2-2.5)C,&1s<t<2s,\\(17.5+5t)C,&2s\le t \le 4s,\\(25t-2.5t^2-22.5)C,&4s<t\le5s \end{cases} $$
so
$$Q\arrowvert_{t=1s}=10C,Q\arrowvert_{t=3s}=32.5C,Q\arrowvert_{t=5s}=40C$$

### 1.10

$$ Q=\int_{t0}^{t}i=0.15A $$

### 1.11

$$Q=\int_{t0}^{t}i=3888C,w=\int_{to}^{t}vi\ dt=5832J$$
