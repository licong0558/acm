# 用途
求出整数 $x,y$ 使得 $ax+by=gcd(a,b)$
# 求不定方程$ax+by=c$的整数解
前提：$ c\%gcd(a,b)=0 $
$x,y$ 同乘 $c\over{gcd(a,b)}$ 即为解
# 最小整数解
求得特解$x,y$后
$\begin{cases}
x_t=x+{b\over{gcd(a,b)}}\times t \\
y_t=y-{a\over{gcd(a,b)}}\times t \\
\end{cases}$
设$m={b\over gcd(a,b)}$,x的最小整数解为`(x%m+m)%m`
