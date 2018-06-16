---
plugins:
  - mathjax
  - katex
pluginsConfig: null
---

两直线方程可以表示为  
$$l_1=a_0x+b_0y+c$$  
$$l_2=a_1x+b_1y+c$$  
联立得

$$ \begin{bmatrix}  
   a_0 & b_0 & c_0 \\
   a_1 & b_1 & c_1  
  \end{bmatrix}\times
  \begin{bmatrix}
  x\\
  y\\
  1
  \end{bmatrix}=0$$

$$\begin{cases}
D=a_0b_1-a_1b_0 \\
x= {b_0c_1-b_1c_0\over D} \\
y= {a_1c_0-a_0c_1\over D}
\end{cases}$$

$$D=0$$ 时两直线平行
