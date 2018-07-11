# 组合数取模

## 杨辉三角（范围较小）

## 阶乘预处理（m，n必须小于p）

## 卢卡斯定理



$$
C_m^n\equiv \prod_{i=0}^{k}C_{m_i}^{n_i} \pmod p
$$

其中$$ m_i,n_i $$ 表示$$ p $$ 进制下$$ m,n $$ 的第 $$ i $$ 位

$$
m=\sum{i=0}^{k}m_ip^i\\n=\sum{i=0}^{k}n_ip^i
$$

因此可以用递归的解法求组合数

$$
C_m^n=\begin{cases}C_{m\%p}^{n\%p}\times C_{m/p}^{n/p} & \text{n>=p || m>=p} \\0 & \text{p>n>m}\\fac[m]\times faci[m-n]\times faci[n]& \text{else}\end{cases}
$$

```text

```

当$$ n,m $$超过$$ p $$时，就不能再使用阶乘和阶乘逆元的前缀积来计算，因为当分母为$$ p $$的倍数时，模后的值为0，无法计算逆元。必须使用卢卡斯定理处理到两值均小于p。

