# LCP 22. ccw6C7 | 黑白方格画

## Question description

<!--If you want to use the English description, use  instead-->
小扣注意到秋日市集上有一个创作黑白方格画的摊位。摊主给每个顾客提供一个固定在墙上的白色画板，画板不能转动。画板上有 `n * n` 的网格。绘画规则为，小扣可以选择任意多行以及任意多列的格子涂成黑色（选择的整行、整列均需涂成黑色），所选行数、列数均可为 0。

小扣希望最终的成品上需要有 `k` 个黑色格子，请返回小扣共有多少种涂色方案。

注意：两个方案中任意一个相同位置的格子颜色不同，就视为不同的方案。

**示例 1：**
>输入：`n = 2, k = 2`
>
>输出：`4`
> 
>解释：一共有四种不同的方案：
>第一种方案：涂第一列；
>第二种方案：涂第二列；
>第三种方案：涂第一行；
>第四种方案：涂第二行。

**示例 2：**
>输入：`n = 2, k = 1`
> 
>输出：`0`
> 
>解释：不可行，因为第一次涂色至少会涂两个黑格。

**示例 3：**
>输入：`n = 2, k = 4`
> 
>输出：`1`
>
>解释：共有 2*2=4 个格子，仅有一种涂色方案。

**限制：**
- `1 <= n <= 6`
- `0 <= k <= n * n`




## Note

此题关键在于横列可以有交叉点，用i表示所用行数，j表示所用列数，则n*（i+j）表示用了所有的行数和列数的棋子，再减去重复使用的交叉点i*j即表示平面看上去所有的棋子个数k，剩下就是计算组合C(n,i)和C(n,j),有多种方式选择，比赛我给实现用的迭代版。



https://leetcode-cn.com/problems/ccw6C7/solution/shu-xue-tui-dao-by-sunrise-z/


## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def paintingPlan(self, n: int, k: int) -> int:
        if k in (0,n*n):return 1
        def get(n,a):
            #计算组合公式递归版
            def helper(n):
                if n<=1:return 1
                return  n*helper(n-1)
            return helper(n)/(helper(a)*helper(n-a))        
        ans=0
        for i in range(n):
            for j in range(n):
                if n*(i+j)-(i*j) ==k:
                    ans+=get(n,i)*get(n,j)             
        return int(ans)


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ccw6C7/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ccw6C7/description/)

Solution: [LeetCode](https://leetcode.com/articles/ccw6C7/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ccw6C7/)

[回到目录](../README.md)