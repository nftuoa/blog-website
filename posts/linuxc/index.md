
---
title: "《Linux C编程一站式学习》习题解答"
author: "Oscar Tuo"
date: "2025-01-27"
categories: [programming]
---

**学这本书主要是为了满足[ysyx](http://ysyx.oscc.cc)的要求,故会先以一个较快的速度更新完ysyx要求的部分(第1-9章, 第11-16章, 第21章, 第23-25章, 以及第26章第1节),未经特殊标记的程序默认采用C17标准编译通过。**

编译环境:AMD Ryzen 7 7840HS,EndeavourOS x86-64,Linux 6.12.10,gcc 14.2.1(标了C23的用的是15.0)；跑不通的建议先想想是不是Windows的问题,再想想是不是英特尔的问题,再想想是不是Clang的问题

你可以在这里读到这本书: https://akaedu.github.io/book/index.html 



## 第二章
### 习题2-2
```c
#include <stdio.h>
int main(void)
{
	printf("%%\n");
}
```
### 习题2-5
```c
#include <stdio.h>
#include <math.h>
int main(void)
{
	printf("%d\n",(int)ceil(17.0/4));
}
```
## 第三章

### 习题3-3

#### 1.
不能increment里的x是形参，不会影响传进去的实参

#### 2.
printf在stdio.h里，不把stdio.h给include进去的话printf没有定义

## 第四章

### 习题4-1
错误:if的条件满足后会执行一个空语句，下面那行并没有被if的判定所限制
\
编译能通过:没有语法错误

### 习题4-2

#### 1.
x%10;(int) (x%100)/10

#### 2.
```c
void printdigit(int x)
{
	printf("%d,%d\n",x%10,(int) (x%100)/10)
}
```

### 习题4-3

#### 1.
```c
if (x>=10 || x<=0)
	printf("x is out of range\n");
```

#### 2.
```c
if (x<=0 && y<=0)
	printf("test failed!\n");
else
	printf("test ok!\n");
```

#### 3.
```c
y=1 || x=1
```

#### 4.

**总之是第二个**



## 第五章

### 习题5-1

#### 1.

*请用C23编译*
```c

bool is_leap_year(int year)
{
	if(year%4!=0 || (year%100==0 && year%400!=0))
		return false;
	else
		return true;
}

```

#### 2.
```c
#include <math.h>
double myround(double x)
{
  if(x<0)
    return ceil(x-0.5);
  else 
    return floor(x+0.5);
}
```
*用gcc编译的话请加入-lm参数,我也不知道这个大哥为什么默认不会去找math.h*

### 习题5-3

#### 1.
```c
int euclid(int a, int b)
{
	if (a%b==0)
		return b;
	else
		return(euclid(b,a%b));
}
```
证明交给屏幕前的各位未来的yau们自己完成(

#### 2.
```c
int fibo(int n)
{
	if (n==0||n==1)
		return 1;
	else
		return(fibo(n-1)+fibo(n-2));
}
```

## 第六章

### 习题6-1

#### 1.
*用循环写递归本质上就是让你的脑子递归*

##### (1).
```c
int euclid(int a,int b)
{int remain = 1;
while (remain!=0)
{
	remain = a%b;
	a = b;
	b = remain;
}
return a;}
```

##### (2).
```c
int fib(int n){
int fibo[100];
fibo[0]=1;
fibo[1]=1;
for(int i = 2;i<=n;i++)
{
	fibo[n]=fibo[n-2]+fibo[n-1];
}}
```

#### 2.
```c
int nine(void){
int nines=0;
for(int i = 1;i<101;i++)
{
	if ((i%10)==9||((int) i/10) == 9)
	nines++;
}
return nines;
```

### 习题6-4

#### 1.
```c
#include <stdio.h>
int is_prime(int n)
{
	int i=2;
	while(i < n && (n % i) !=0)
		i++;
	if (i == n)
		return 1;
	else
		return 0;
}

int main(void)
{
	int i;
	for (i = 1; i <= 100; i++) {
		if (is_prime(i))
		printf("%d\n", i);
	}
	return 0;
}
```

#### 2.
可能会有某几次循环表达式3没有被执行

### 习题6-5

#### 1.
```c
#include <stdio.h>

int main(void)
{
	int i, j;
	for (i=1; i<=9; i++) {
		for (j=1; j<=9; j++)
			if(j<=i)	
			printf("%d\t", i*j);
		printf("\n");
	}
	return 0;
}
```

#### 2.
```c
void diamond(int n,char s)
{
  if(n%2==0)return;
  for(int i = 1;i<=n;i+=2)
  {
    for(int t = 0;t<(n-i)/2;t++)printf(" ");
    for(int t = 0;t<i;t++)
      printf("%c",s);
    printf("\n");
  }
  for(int i = n-2;i>0;i-=2)
  {
    for(int t = 0;t<(n-i)/2;t++)printf(" ");
    for(int t = 0;t<i;t++)
      printf("%c",s);
    printf("\n");
  }
}
```

## 第七章

### 习题7-2

#### 1.

```c
#include <stdio.h>
struct complex_struct{
	double x,y;
};
void output_complex(struct complex_struct a){
	if(a.x!=0)
  {
    printf("%.2lf",a.x);
    if(a.y!=0)printf("+");
    else printf("\n");
  }

  if(a.y!=0)
	printf("%.2lfi\n",a.y);
}
int main(void)
{
	struct complex_struct a = {1,2};
	struct complex_struct b = {0,1};
	struct complex_struct c = {1,0};
	output_complex(a);
	output_complex(b);
	output_complex(c);
}
```

#### 2.

```c
#include <stdio.h>

struct rational{
  int num,deno;
};


int euclid(int a, int b)
{
	if (a%b==0)
		return b;
	else
		return(euclid(b,a%b));
}
struct rational elliminate(struct rational c)
{
  int factor = euclid(c.num,c.deno);
  c.num = c.num/factor;
  c.deno = c.deno/factor;
  return c;
}
struct rational add_rational(struct rational a, struct rational b)
{
  struct rational sum;
  sum.num = a.num*b.deno + b.num*a.deno;
  sum.deno = a.deno*b.deno;
  sum = elliminate(sum);
  return sum;
}
struct rational sub_rational(struct rational a, struct rational b)
{
  struct rational differ;
  differ.num = a.num*b.deno - b.num*a.deno;
  differ.deno = a.deno*b.deno;
  differ = elliminate(differ);
  return differ;
}
struct rational mul_rational(struct rational a, struct rational b)
{
  struct rational product;
  product.num = a.num*b.num;
  product.deno = a.deno*b.deno;
  product = elliminate(product);
  return product;
}
struct rational div_rational(struct rational a, struct rational b)
{
  struct rational quotient;
  quotient.num = a.num*b.deno;
  quotient.deno = a.deno*b.num;
  quotient = elliminate(quotient);
  return quotient;
}
struct rational make_rational(int a, int b)
{
  struct rational c;
  c.num = a;
  c.deno = b;
  return c;
}
void print_rational(struct rational a)
{
  if(a.deno!=1)
    printf("%d/%d\n",a.num,a.deno);
  else
    printf("%d\n",a.num);
}
int main(void)
{
	struct rational a = make_rational(1, 8); /* a=1/8 */
	struct rational b = make_rational(-1, 8); /* b=-1/8 */
	print_rational(add_rational(a, b));
	print_rational(sub_rational(a, b));
	print_rational(mul_rational(a, b));
	print_rational(div_rational(a, b));

	return 0;
}

```

### 习题7-3

#### 1.

```c

#include <stdio.h>
#include <math.h>

enum coordinate_type { RECTANGULAR, POLAR };
struct complex_struct {
	enum coordinate_type t;
	double a, b;
};
struct complex_struct make_from_real_img(double x, double y)
{
	struct complex_struct z;
	z.t = RECTANGULAR;
	z.a = x;
	z.b = y;
	return z;
}
struct complex_struct make_from_mag_ang(double r, double A)
{
	struct complex_struct z;
	z.t = POLAR;
	z.a = r;
	z.b = A;
	return z;
}

double real_part(struct complex_struct in)
{
  if (in.t == RECTANGULAR)
    return in.a;
  else 
    return (in.a*cos(in.b));
}

double img_part(struct complex_struct in)
{
  if (in.t == RECTANGULAR)
    return in.b;
  else 
    return (in.a*sin(in.b));
}

double magnitude(struct complex_struct in)
{
  if (in.t == POLAR)
    return in.a;
  else 
    return sqrt(in.a*in.a+in.b*in.b);
}

double angle(struct complex_struct in)
{
  if (in.t == POLAR)
    return in.b;
  else 
    return atan(in.b/in.a);
}

int main(void)
{
  struct complex_struct a = make_from_real_img(2,3);
  struct complex_struct b = make_from_mag_ang(1,2);
  printf("%lf %lf %lf %lf %lf %lf %lf %lf\n",real_part(a),real_part(b),img_part(a),img_part(b),magnitude(a),magnitude(b),angle(a),angle(b));
  return 0;
}

```

*使用gcc编译时请加入-lm指令，main函数主要是用来测试*

#### 2.

{{< asciinema "enumtest.cast" cols="80" rows="15" autoPlay="true" speed="4" theme="dracula" poster="npt:1:23" >}}

原因:enum里的RECTANGULAR被后边的初始化语句在main里给覆盖了，而POLAR则还是定义的2