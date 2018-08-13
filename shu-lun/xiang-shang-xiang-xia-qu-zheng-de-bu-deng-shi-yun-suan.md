# 向上向下取整的不等式运算

## 向下取整（floor）

以下各式中除法默认为向下取整的整数除法（ $$\lceil\quad \rceil$$ 标注的除外\)

$$
{a\over b}\ge c \implies \begin{cases}a\ge b\times c\\ b\le {a\over c}\end{cases} \\ {a\over b}\le c \implies \begin{cases}a\le b\times c+b-1\\ b\ge {a\over {c+1}}+1\end{cases}
\\
a\times b\ge c \implies 
\begin{cases}
a\ge \frac{c}{b} & b|c \\
a>\frac{c}{b} & else
\end{cases}
\\
a\times b <c \implies
\begin{cases}
a< \frac{c}{b} & b|c \\
a\le\frac{c}{b} & else
\end{cases}
$$

 

## 向上取整（ceil）

对于$$\lceil {a\over b}\rceil$$可以转化成$${a+b-1}\over b$$利用向下取整的方法运算

