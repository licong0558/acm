# 莫比乌斯反演

## 莫比乌斯函数

### 定义

莫比乌斯函数 $$\mu(n) $$的定义：  
设 $$n = p_1 ^ {k_1} \cdot p_2 ^ {k_2} \cdot\cdots\cdot p_m ^ {k_m}$$ ​​​​，其中 $$p$$ 为素数，则定义如下： 

 $$\mu(n) = \begin{cases} 1 & n = 1 \\ (-1) ^ m & \prod\limits_{i = 1} ^ {m} k_i = 1 \\ 0 & \textrm{otherwise}(k_i \gt 1) \end{cases}$$ 

可知有平方因子的数的莫比乌斯函数值为 $$0$$ 。

### 生成

与线性筛类似，每一个数的值由他的最大因子生成。

```cpp
const ll LIM= 1e5;
ll prime[LIM+100],cnt;
bool isprime[LIM+100];
ll mu[LIM+100];
void linear()
{
    cnt=0;
    memset(isprime,1,sizeof(isprime));
    isprime[1]=false; mu[1]=1;
    for(int i=2;i<=LIM;i++)
    {
        if(isprime[i]){prime[cnt++]=i; mu[i]=-1;}
         for(int j=0;j<cnt&&i*prime[j]<=LIM;j++)
         {
             if(i*prime[j]>LIM) continue;
            isprime[i*prime[j]]=false;
            if(i%prime[j]==0){ break; mu[i*prime[j]]=0;}
            else mu[i*prime[j]]=mu[i]*-1;
        }
    }
}
```

### 性质

 **性质一：**莫比乌斯函数是积性函数。

$$\mu(a)\mu(b) = \mu(a\cdot b), a\perp b$$ 

 **应用：**根据这一性质，我们可以采取线性筛法，用  $$O(n)$$ 的时间预处理出所有 $$[1, n]$$内的莫比乌斯函数值。  
质数的值为 $$-1$$ ，如果一个数存在某个质因子的指数不为 $$1$$ ，那么它将会被筛为 $$0$$ （值得注意的是，只有数存在最小质因子的指数大于 $$1$$ 时，它才会被**直接**筛为 $$0$$ ，其余的情况是由 $$ \mu(d) = -\mu(i) $$ 来完成的）。  
每个数仅被其最小质因子筛去，故复杂度为 $$O(n)$$ 。

 **性质二：**  

$$
\sum_{d\mid n}\mu(d) = [n = 1]​
$$

**证明：**当 n = 1 时有 $$ \mu(1) = 1$$ ，显然成立。否则设 $$n = p_1 ^ {k_1} \cdot p_2 ^ {k_2} \cdot\cdots\cdot p_m ^ {k_m}$$ ， $$d = p_1 ^ {x_1} \cdot p_2 ^ {x_2} \cdot\cdots\cdot p_m ^ {x_m}$$ 根据 $$\mu$$ 的定义，只需考虑 $$x_i = 0$$ 或 $$ x_i = 1$$ 的情况。我们设 $$d$$ 中存在 $$r$$ 个 $$x_i$$ 为 $$1$$ ，那么有：

$$
\sum_{d\mid n}\mu(d) = \sum_{r = 0}^m\binom m r(-1)^r(n \neq 1)​
$$

根据[二项式定理](https://en.wikipedia.org/wiki/Binomial_theorem)：

$$
(x+y)^{n}=\sum _{k=0}^{n}\binom n kx^{n-k}y^{k}
$$

我们令 $$ x = 1, y = -1$$ ，即得证：

$$
\sum_{r = 0}^m\binom m r(-1)^r = (1 - 1)^m = 0(n \neq 1)
$$

此公式运用的很多，在求 $$\gcd = 1$$或是用杜教筛求前缀和的时候都用的到。

##  莫比乌斯反演

$$
F(n)=\sum_{d|n}f(n) \\ f(n)=\sum_{d|n}\mu({n\over d})F(d)=\sum_{d|n}\mu(d)F({n\over d})
$$

### 证明

$$
f(n)=\sum_{d|n}\mu(d)\sum_{i|{n\over d}}f(i) \\
=\sum_{d|n}f(d)\sum_{i|{n\over d}}\mu(i)\\
​=f(n)
$$

式中累加的变换是因为整个式子的意思是所有满足 $$di|n$$ 的 $$<d,i>$$ 对 $$\mu(d)f(i)$$ 之和。

### 另一种形式

$$
F(n)=\sum_{n|d}f(n) \\
f(n)=\sum_{n|d}\mu({d \over n})F(d)
$$

### 证明

$$
f(n)=\sum_{n|d}\mu({d \over n})\sum_{d|i}f(i)\\
=\sum_{n|i}f(i)\sum_{d|{i\over n}}\mu(d)\\
=f(n)
$$

累加变换与上式类似，设 $$a=\frac{d}{n}$$  ，实际上是求 $$\sum\mu(a)f(i) \quad(na|i)$$ 

## 应用

### 求 $$[1,a],[1,b]$$ 互质数的对数

$$F(n)$$ :有公因数为 $$n$$ 的对数

$$f(n)$$ : $$gcd$$ 为 $$n$$ 的对数

得到：

$$
F(n)=\sum_{n|d}f(d)
$$

**可以拓展到求** $$gcd=k$$ **的对数**

