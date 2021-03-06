# 错误总结



每天看一遍

* 留意特殊情况，例如推出的式子分母项为0（如等比数列q为1）
* 图论问题邻接表的大小，有时边数远大于点数，或者对每条边需要插入正反两条边，需要看清楚开多大的邻接表。
* 一个题目中不同数组可能需要不同的大小，不要弄混。
* 编码时牢记每个变量的意义，不要用混。
* 位与或的优先级只比逻辑与或高1，比大于小于等于要低，使用时务必加上括号。
* 移位运算一律使用`1LL<<`
* 移位运算优先级比加减乘除低
* 永远考虑0，1等特殊情况，对每个值可能为0，1的变量都要加以考虑。
* 时间吃紧的题目，看到多组数据一定要尽可能节省的初始化，BIT可以更改update上限，尤其是在ZOJ上。
* 内存吃紧时把`ll`改回`int`
* 对于某些存疑的结论，要考虑在可接受的复杂度增加情况下放弃，结论可能是错的。
* 手动生成的字符串给末尾加上`\0`
* WA时不要只检查关键部分代码逻辑，可能是一些不重要部分的低级错误。
* 读题时要逐字读，不要偷懒
* 如果对题意不确定，时间充裕的话一定要读样例。
* 能压位就不要递归，递归太慢了。
* 更改代码时考虑更改一处可能会影响另一处。
* 矩阵快速幂矩阵内的数是负数的话要处理

