动态规划是算法中最常见的一类问题之一，其解题思路常常为，将大问题分解为小问题，
并且建立起通过解决小问题到解决大问题的对应关系来得到最终的答案，
一旦找了分解问题和合并小问题答案的方程，问题本身就迎刃而解。然而，
对于具体实现来说，从找到对应关系到最优的实现方式之间往往有着一些小技巧。

动态规划的关键点：
动态规划和递归或者分治没有根本上的区别（关键看有无最优的子结构）
共性：找到重复子问题
差异性：最优子结构、中途可以淘汰次优解

1.最优子结构：
opt[n]=best_of(opt[n-1],opt[n-2],....)
2.存储中间状态：opt[i]
3.递推公式（美其名曰状态转换方程或DP方程）：
Fib:opt[i]=opt[n-1]+opt[n-2]
二维路径：opt[i,j]=opt[i+1][j]+opt[i][j+1](且判断a[i][j]是否是空地)

这周的课程有点难以理解，我基本上都是按题解做的，需要多练习练习


