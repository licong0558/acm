# 树链剖分

## 用途

把一颗树映射到线性数据结构上\(线段树），使树上的任意一条路径都能拆分成不超过 $$\log_2n$$ 个重链。然后用线段树维护重链，便可以维护树上的路径修改，查询。

## 注意

信息在点上和信息在边上的处理方法略有不同。
