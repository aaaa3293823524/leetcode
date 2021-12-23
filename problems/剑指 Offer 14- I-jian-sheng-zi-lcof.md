# 剑指 Offer 14- I. jian-sheng-zi-lcof | 剪绳子

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>给你一根长度为 <code>n</code> 的绳子，请把绳子剪成整数长度的 <code>m</code> 段（m、n都是整数，n&gt;1并且m&gt;1），每段绳子的长度记为 <code>k[0],k[1]...k[m-1]</code> 。请问 <code>k[0]*k[1]*...*k[m-1]</code> 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入: </strong>2
<strong>输出: </strong>1
<strong>解释: </strong>2 = 1 + 1, 1 &times; 1 = 1</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>10
<strong>输出: </strong>36
<strong>解释: </strong>10 = 3 + 3 + 4, 3 &times;&nbsp;3 &times;&nbsp;4 = 36</pre>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= n &lt;= 58</code></li>
</ul>

<p>注意：本题与主站 343 题相同：<a href="https://leetcode-cn.com/problems/integer-break/">https://leetcode-cn.com/problems/integer-break/</a></p>


## Note

数学     动态规划





还是 343. 整数拆分 的官方题解写的更清楚

本题说的将绳子剪成m段，m是大于1的任意一个正整数，也就是必须剪这个绳子，至于剪成几段，每一段多长，才能使得乘积最大，这就是要求解的问题了



【解题思路1】动态规划

对于的正整数 n，当 n≥2 时，可以拆分成至少两个正整数的和。令 k 是拆分出的第一个正整数，则剩下的部分是 n−k，n−k 可以不继续拆分，或者继续拆分成至少两个正整数的和。由于每个正整数对应的最大乘积取决于比它小的正整数对应的最大乘积，因此可以使用动态规划求解。



dp数组的含义： dp[i] 表示将正整数 i 拆分成至少两个正整数的和之后，这些正整数的最大乘积。

边界条件： 0 不是正整数，1 是最小的正整数，0 和 1 都不能拆分，因此 dp[0]=dp[1]=0。

状态转移方程：

当 i≥2 时，假设对正整数 i 拆分出的第一个正整数是 j（1≤j<i），则有以下两种方案：



将 i 拆分成 j 和 i−j 的和，且 i−j 不再拆分成多个正整数，此时的乘积是 j×(i−j)；

将 i 拆分成 j 和 i−j 的和，且 i−j 继续拆分成多个正整数，此时的乘积是 j×dp[i−j]。

因此，当 j 固定时，有 dp[i]=max(j×(i−j),j×dp[i−j])。由于 j 的取值范围是 1 到 i−1，需要遍历所有的 j 得到 dp[i] 的最大值，因此可以得到状态转移方程如下：



dp[i]= max_{1≤j<i} {(j×(i−j),j×dp[i−j])}

dp[i]= 

1≤j<i

max

​	

 (j×(i−j),j×dp[i−j])



最终得到 dp[n] 的值即为将正整数 n 拆分成至少两个正整数的和之后，这些正整数的最大乘积。



确定某一位置的dp公式 随着位置滑动 更新最大或最小值 边界   dp代表什么




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int cuttingRope(int n) {
        int[] dp = new int[n + 1];
        for (int i = 2; i <= n; i++) {
            for (int j = 1; j < i; j++) {
                dp[i]= Math.max(dp[i], Math.max(j * (i - j), j * dp[i - j]));
            }
        }
        return dp[n];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/jian-sheng-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/jian-sheng-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/jian-sheng-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/jian-sheng-zi-lcof/)

[回到目录](../README.md)