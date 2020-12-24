# 441. arranging-coins | 排列硬币

## Question description

<!--If you want to use the English description, use <p>You have a total of <i>n</i> coins that you want to form in a staircase shape, where every <i>k</i>-th row must have exactly <i>k</i> coins.</p>
 
<p>Given <i>n</i>, find the total number of <b>full</b> staircase rows that can be formed.</p>

<p><i>n</i> is a non-negative integer and fits within the range of a 32-bit signed integer.</p>

<p><b>Example 1:</b>
<pre>
n = 5

The coins can form the following rows:
¤
¤ ¤
¤ ¤

Because the 3rd row is incomplete, we return 2.
</pre>
</p>

<p><b>Example 2:</b>
<pre>
n = 8

The coins can form the following rows:
¤
¤ ¤
¤ ¤ ¤
¤ ¤

Because the 4th row is incomplete, we return 3.
</pre>
</p> instead-->
<p>你总共有&nbsp;<em>n&nbsp;</em>枚硬币，你需要将它们摆成一个阶梯形状，第&nbsp;<em>k&nbsp;</em>行就必须正好有&nbsp;<em>k&nbsp;</em>枚硬币。</p>

<p>给定一个数字&nbsp;<em>n</em>，找出可形成完整阶梯行的总行数。</p>

<p><em>n&nbsp;</em>是一个非负整数，并且在32位有符号整型的范围内。</p>

<p><strong>示例 1:</strong></p>

<pre>
n = 5

硬币可排列成以下几行:
&curren;
&curren; &curren;
&curren; &curren;

因为第三行不完整，所以返回2.
</pre>

<p><strong>示例 2:</strong></p>

<pre>
n = 8

硬币可排列成以下几行:
&curren;
&curren; &curren;
&curren; &curren; &curren;
&curren; &curren;

因为第四行不完整，所以返回3.
</pre>




## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def arrangeCoins(self, n: int) -> int:
        left, right = 0, n
        while(True):
            if left>right:
                return right
            mid = (left+right)//2
            count = (1+mid)*mid/2
            if count == n:
                return mid
            elif count<n:
                left = mid+1
            else:
                right = mid-1


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/arranging-coins/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/arranging-coins/description/)

Solution: [LeetCode](https://leetcode.com/articles/arranging-coins/)  /  [LeetCode中国](https://leetcode-cn.com/articles/arranging-coins/)

[回到目录](../README.md)