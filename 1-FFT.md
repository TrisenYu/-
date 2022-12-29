## FFT
规定讨论的序列长度必然是 $2$ 的非负整数次幂。对于最后的乘积，可以简单记成下面的形式。
$$
\begin{aligned}
\boldsymbol{C}=
\begin{bmatrix}
c_0\\
c_1 \\
c_2 \\
\vdots \\
c_{m-1}
\end{bmatrix}
=\dfrac{1}{m}\begin{bmatrix}
1 &1           &1           &\cdots &1\\
1 &\omega^{-1} &\omega^{-2} &\cdots &\omega^{1-m}\\
1 &\omega^{-2} &\omega^{-4} &\cdots &\omega^{2-2m} \\
\vdots &\vdots &\vdots      &\ddots &\vdots\\
1 &\omega^{1-m}&\omega^{2-2m} &\cdots &\omega^{-(m-1)^2}
\end{bmatrix}\cdot
\begin{bmatrix} 
f_0\cdot g_0\\
f_1\cdot g_1 \\
f_2\cdot g_2 \\
\vdots \\
f_{m-1}\cdot g_{m-1}
\end{bmatrix}
\end{aligned}
$$
其中 $f_0,f_1,\ldots,f_{m-1};g_0,g_1,\ldots,g_{m-1}$ 分别代表 $f(1),f(\omega),\ldots,f(\omega^{m-1});g(1),g(\omega),\ldots,g(\omega^{m-1})$。

所以只要正变换能解决，逆变换自然不在话下。另外，有下列复数单位根中有三个等式成立。
$$\begin{align}
&\omega^p=-\omega^{p+\frac{m}{2}} \\
&\omega^m=1
\\& \omega_{2m}^{2p}=\omega_m^p.
\end{align}$$
为了方便，我们将 $(3)$ 式折半运算的记法变为 $\omega^{2^n} \rightarrow \omega_1^{2^{n-1}} \rightarrow \ldots \rightarrow \omega_{n-1}^2\rightarrow \omega_{n}$ 的形式。假如最后算到的长度为 $m=8$ ，那么对于给定的因数 $f$ 运用奇偶划分，就有下面的式子。
$$
\begin{aligned}
f(\omega^p)&=a_0+a_1\omega^{p}+a_2\omega^{2p}+a_3\omega^{3p}+a_4\omega^{4p}+a_5\omega^{5p}+a_6\omega^{6p}+a_7\omega^{7p}
\\&=
\left(a_0+a_2\omega^{2p}+a_4\omega^{4p}+a_6\omega^{6p}\right)
+
\omega^{p}\left(a_1+a_3\omega^{2p}+a_5\omega^{4p}+a_7\omega^{6p}\right)
\\&=
A_0(\omega^{2p})
+\omega^{p}A_1(\omega^{2p})
\\&=
\left(a_0+a_2\omega_1^{p}+a_4\omega_1^{2p}+a_6\omega_1^{3p}\right)
+
\omega^{p}\left(a_1+a_3\omega_1^{p}+a_5\omega_1^{2p}+a_7\omega_1^{3p}\right)
\\&=A_0(\omega_1^{p})
+\omega^{p}A_1(\omega_1^{p})
\\&=
\left((a_0+a_4\omega_1^{2p})+\omega_1^{p}(a_2+a_6\omega_1^{2p})\right)
+
\omega^{p}\left((a_1+a_5\omega_1^{2p})+\omega_1^{p}(a_3+a_7\omega_1^{2p})
\right)
\\&=\left(A_{00}(\omega_1^{2p})+\omega_1^{p}A_{01}(\omega_1^{2p})\right)
+\omega^{p}\left(A_{10}(\omega_1^{2p})+\omega_1^{p}A_{11}(\omega_1^{2p})
\right)
\\&=\left[A_{00}(\omega_2^{p})+\omega_1^{p}A_{01}(\omega_2^{p})\right]
+\omega^{p}\left[A_{10}(\omega_2^{p})+\omega_1^{p}A_{11}(\omega_2^{p})\right]
\\&=\left((a_0+\omega_2^{p}a_4)+\omega_1^{p}(a_2+\omega_2^{p}a_6)\right)
+
\omega^{p}\left((a_1+\omega_2^{p}a_5)+\omega_1^{p}(a_3+\omega_2^{p}a_7)
\right)
\\&=\left[(A_{000}+\omega_2^{p}A_{001})+\omega_1^{p}(A_{010}+\omega_2^{p}A_{011})\right]
+\omega^{p}\left[(A_{100}+\omega_2^{p}A_{101})+\omega_1^{p}(A_{110}+\omega_2^{p}A_{111})\right]
\\
\\
\Rightarrow f(\omega^{p+\frac{m}{2}})&=a_0-a_1\omega^{p}+a_2\omega^{2p}-a_3\omega^{3p}+a_4\omega^{4p}-a_5\omega^{5p}+a_6\omega^{6p}-a_7\omega^{7p}
\\&=
A_0(\omega^{2p})
-\omega^{p}A_1(\omega^{2p})
\\&=\ldots
\\&=\left[(A_{000}+\omega_2^{p}A_{001})+\omega_1^{p}(A_{010}+\omega_2^{p}A_{011})\right]
\boldsymbol{\color{red}-}\omega^{p}\left[(A_{100}+\omega_2^{p}A_{101})+\omega_1^{p}(A_{110}+\omega_2^{p}A_{111})\right]
\end{aligned}
$$
其中 $p\in [0,\dfrac{m}{2}-1]$。$g$ 同理。而考虑整体，由 $f_0,f_1,\ldots,f_{m-1}$ 构成的矩阵有下式。~~虽然无关紧要~~。
$$
\begin{bmatrix} 
f_0\\
f_1 \\
f_2 \\
\vdots \\
f_{m-1}
\end{bmatrix}=
\begin{bmatrix}1 &1 &1 &\cdots &1\\
1 &\omega &\omega^{2} &\cdots &\omega^{m-1}\\
1 &\omega^{2} &\omega^{4} &\cdots &\omega^{2m-2} \\
\vdots &\vdots &\vdots &\ddots &\vdots\\
1 &\omega^{m-1} &\omega^{2m-2} &\cdots &\omega^{(m-1)^2}
\end{bmatrix}\cdot 
\begin{bmatrix} 
a_0\\
a_1 \\
a_2 \\
\vdots \\
a_{m-1}
\end{bmatrix}
$$
结合刚刚得到的奇偶划分式，只需要扫完前一半的序列，后一半序列就自然能在当前一层中计算得到。这部分时间是 $O(n)$ 的。同时，又由于是递归计算，从最深一层算回最后的结果，显然是需要 $O(\log n)$ 的。综合上述结论，时间复杂度从 $O(n^2)$ 降到 $O(n\log n)$。

而这便是整个算法最抽象的部分。因为程序是一次性算好要求的 $f_0\sim  f_{m-1}$。

接下来就是写代码的时光了。
```cpp{.line-numbers}
using db = long double;
const db pi=(db)acos(-1);
struct cp{
    db x,y;
    cp(xx=0,yy=0):x(xx),y(yy){}
    cp operator + (const cp& a){return cp(a.x+x,a.y+y);}
    cp operator - (const cp& a){return cp(x-a.x,y-a.y);}
    cp operator * (const cp& a){return cp(x*a.x-y*a.y,x*a.y+y*a.x);}
};
int N;
void fft(cp a[],int len,int sig=1)
{
    if(len==1)return;
    int mid=len>>1;
    static cp b[N];
    for(int i=0;i<mid;++i)b[i]=a[i<<1],b[i+mid]=a[i<<1|1];
    for(int i=0;i<n;++i)a[i]=b[i];
    fft(a,mid,sig),fft(a+mid,mid,sig);
    for(int i=0;i<mid;++i)
    {
        cp w(cos(2*pi*i/len),sig*sin(2*pi*i/len));
        b[i]=a[i]+w*a[i+mid], b[i+mid]=a[i]-w*a[i+mid];
    }
    for(int i=0;i<n;++i)a[i]=b[i];
}
```
若还不能理解整套算法是怎么样通过几个单位根算出要求的 $m$ 个函数值的，可以输出程序运行的过程理解。这里给出结果序列是 $32$ 位时的运行情况。
```cpp
4655611
544545487878412
原序列每一个数的顺序：0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31
交换后每一个数的位置：0 16 8 24 4 20 12 28 2 18 10 26 6 22 14 30 1 17 9 25 5 21 13 29 3 19 11 27 7 23 15 31
w:-1+(-3.21629e-16)i // w_5 ，从 (1,0) 开始到 w_4 之前每次自乘，以下同理
0 1 // 交换后数字的下标 代表的就是原序列第0个数和第16个数参与运算，然后覆盖结果当前的第0位与第1位。以下同理
2 3 // a*2<- a8+a24, a*3<- a8-a24
4 5 // a*4<- a4+a20, a*5<- a4-a20
6 7 // a*6<- a12+a28,...
8 9 // a*8<- a2+a18,...
10 11
12 13
14 15
16 17
18 19
20 21
22 23
24 25
26 27
28 29
30 31
w:-1.60814e-16+(1)i // w_4
0 2 // a.0<- a*0+a*2 = (a0+a16)+(a8+a24),   a.2<a*0-a*2
1 3 // a.1<- a*1+w_4a*3 = (a0-a16)+w_4(a8-a24),   a.3<-a*1-w_4a*3
4 6 // a.4<- a*4+a*6 = (a4+a20) + (a12+a28),  a.6<- a*4-a*6 = a4+a20 - (a12+a28)
5 7 // a.5<- a*5+w_4a*7 = (a4-a20) + w_4(a12-a28), ...
8 10 // a.8<- a*8+a*10= (a2+a18)+(a10+a26), ...
9 11
12 14
13 15
16 18
17 19
20 22
21 23
24 26
25 27
28 30
29 31
w:0.707107+(0.707107)i // w_3
0 4 // A0<- a.0+a.4 = (a0+a16) +(a8+a24)+ (a4+a20)+(a12+a28) A4<-(a0+a16) +(a8+a24)-[(a4+a20)+(a12+a28)] 
1 5 // A1 <- a.1+w_3a.5= [(a0-a16)+w_4(a8-a24)] + w_3[(a4-a20) + w_4(a12-a28)],...
2 6 // A2 <- a.2+w_3^2·a.6,  A6 <- a.2-w_3^2·a.3
3 7 // ...
8 12// A8 <- a.8+a.12 = (a2+a18)+(a10+a26) + (a6+a22)+(a14+a30)
9 13
10 14
11 15
16 20
17 21
18 22
19 23
24 28
25 29
26 30
27 31
w:0.92388+(0.382683)i // w_2
0 8 // A0<-(a0+a16) +(a8+a24)+ (a4+a20)+(a12+a28)+(a2+a18)+(a10+a26) + (a6+a22)+(a14+a30)
1 9 // A1<-{[(a0-a16)+w_4(a8-a24)]+w_3[(a4-a20) + w_4(a12-a28)]}+ w_2{[(a2-a18)+w_4(a10-a26)]+w_3[(a6-a22)+w_4(a14-a30)]} 
2 10 
3 11 
4 12
5 13
6 14
7 15
16 24 
17 25
18 26
19 27
20 28
21 29
22 30
23 31
w:0.980785+(0.19509)i // w
0 16 // f(0)=A0+A16=(a0+a16)+(a8+a24)+(a4+a20)+(a12+a28)+(a2+a18)+(a10+a26)+(a6+a22)+(a14+a30)+后一半
1 17 // f(1)
2 18 // 
3 19 // 
4 20 // 
5 21
6 22
7 23
8 24
9 25
10 26
11 27
12 28
13 29
14 30
15 31
//略去两数相乘的结果。
```
![avatar](FFTfor.drawio.png)
然后考虑优化。`static cp b[leng]` 和递归有时候很搞人。所以可以~~丧心病狂~~的省略掉它们。具体的做法如下。

注意到算的时候是把原始序列 $\{0,1,2,3,4,5,6,7\}$ 转变成 $\{0,4,2,6,1,5,3,7\}$，然后合并回来。所以可以在处理之前先把这工作做了。然后再整体算回去。
对于变换的规律，可以展开他们的二进制数来看。对于位置到位置的变换，有：
$$
\begin{aligned}&
000 \leftarrow 000 \\&
001 \leftarrow 100 \\&
010 \leftarrow 010 \\&
011 \leftarrow 110 \\
\\& 100 \leftarrow 001
\\& 101 \leftarrow 101
\\& 110 \leftarrow 011
\\& 111 \leftarrow 111
\end{aligned}
$$
显然只是二进制数上的反转。那么，可以给出最初的反转方案。
```cpp
int I=i;
while(i)rev[I]<<=1,rev[I]|=i&1,i>>=1;
```
但，显然不可能对每个数都这么操作一次。我们需要更快的办法。我们可以利用先前求得的 `rev[i>>1]` 来 dp，毕竟我们计算机在算好了先前反转的块后就能偷懒了。这个时候，就可以有下面的式子。
```cpp
for(int i=0;i<tot;++i)rev[i]=(rev[i>>1]>>1)|((i&1)<<(bits-1));
```
先前算好的 `rev[i>>1]` 右移一位后，**或**上当前左移了 `bits-1` 位的 `i&1`，即为我们要求的 `rev[i]` 了。相应地，快速傅里叶变换的函数就能写成下面的样子。
```cpp{.line-numbers}
void fft(cp a[],int len,int sig=1)
{
    for(int i=0;i<len;++i)if(i<rev[i])swap(a[i],a[rev[i]]);

    for(int mid=1;mid<len;mid<<=1){ // 从分到最后的最小长度枚举回整个序列的一半
        cp w(cos(pi/mid,sig*sin(pi/mid)));
        for(int i=0;i<len;i+=mid*2) // 枚举合成一块的长度，i是处理到当前块的下标
        {
            cp w0(1,0);
            for(int j=0;j<mid;j++,w0*=w) // 只需要枚举前半部分，后一半序列自然会算出来。
            {
                auto x=a[i+j],y=w0*a[i+j+mid];
                a[i+j]=x+y,a[i+j+mid]=x-y;
            }
        }
    }
}
int main()
{
    //...
    for(int i=0;i<tot;++i)rev[i]=(rev[i>>1]>>1)|((i&1)<<(bits-1));
    fft(a,tot);
}
```
最后对于求答案的数位，可以以 $999 \times 9998$ 和 $9999 \times 9998$ 的情况来考虑。显然，总是有 $\text{len}_c< \text{len}_a+\text{len}_b$。那么对于非负整数二次幂而言，需要始终满足下面的条件才行。
```cpp
int bit=0,tot=0;
while((1<<bits)<n+m+1)bits++;
tot=1<<bits;
```
