# 费马小定理

## 内容

设$$ p $$是一个质数，则

$$a^p\equiv a\pmod p \implies a^{p-1}\equiv 1\pmod p \implies a^{p-2}\equiv a^{-1} \pmod p$$

## 证明

考虑二项式系数 $$ \tbinom {p}{n}={\tfrac {p!}{n!(p-n)!}} $$，n不为p或0，由于分子有质数p，但分母不含p，故分子的p能保留，不被约分而除去，即$$ {\tbinom {p}{n}} $$恒为p的倍数。再考虑$$ (b+1)^p $$的二项式展开，模p，则

![](../.gitbook/assets/image%20%281%29.png)

![](../.gitbook/assets/image%20%282%29.png)

令b=a-1，即得$$ a^p\equiv a\pmod p $$

## 应用

### 求逆元

$$a^{p-2}\equiv a^{-1} \pmod p$$

### 求幂

$$a^b\equiv a^{b\%(p-1)} \pmod p$$

```text

```

