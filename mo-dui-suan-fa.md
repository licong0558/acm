# 莫队算法

对于序列上的区间询问问题，如果从$$ [l, r][l,r] $$的答案能够 $$O(1)$$ 扩展到 $$[l - 1, r], [l + 1, r],[l, r + 1],[l, r - 1][l−1,r],[l+1,r],[l,r+1],[l,r−1]$$  的答案，那么可以在 $$O(n\sqrt n)O(n√​n​​​) $$ 的复杂度内求出所有询问的答案。

**实现：**离线后排序，顺序处理每个询问，暴力从上一个区间的答案转移到下一个区间答案。  
**排序方法：**设定块的长度为$$S$$ ，按照 $$(\lfloor\frac l S\rfloor, r)$$ 二元组从小到大排序。  
**复杂度分析：**设序列长度为 $$n$$ 则有 $$n\over S$$ 块，询问个数为 $$m$$ 。可以发现从 $$ (l_1, r_1)(l​1​​,r​1​​)$$ 转移到 $$ (l_2, r_2)(l​2​​,r​2​​) $$ 的代价为他们之间的曼哈顿距离。

对于每一个询问序列中的每一个块（第一关键字相同），整个块内纵坐标最多变化 $$n$$ 长度（纵坐标必然单调不减） $$O({n\over S}*n)$$ 。

对于每个询问，横坐标最多变化 $$S \quad O(mS)$$ 。

一共有 $$\frac n S$$​个块，相邻块之间转移的复杂度为 $$O(n) \quad O(\frac n S*n)$$ 。

所以复杂度为 $$O(\frac {n^2} S + mS + \frac {n^2} S)$$ ,不妨让 $$n,m$$ ,  同阶，取 $$ S = \sqrt n$$ ​​​ 时可达到最优复杂度 $$O(n\sqrt n)$$ 

