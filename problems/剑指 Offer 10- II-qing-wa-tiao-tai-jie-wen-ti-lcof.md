# 剑指 Offer 10- II. qing-wa-tiao-tai-jie-wen-ti-lcof | 青蛙跳台阶问题

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 <code>n</code>&nbsp;级的台阶总共有多少种跳法。</p>

<p>答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 2
<strong>输出：</strong>2
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>n = 7
<strong>输出：</strong>21
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>n = 0
<strong>输出：</strong>1</pre>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 100</code></li>
</ul>

<p>注意：本题与主站 70 题相同：<a href="https://leetcode-cn.com/problems/climbing-stairs/">https://leetcode-cn.com/problems/climbing-stairs/</a></p>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int numWays(int n) {
        int[] a=new int[101];
        a[0]=1;a[1]=1;
        for(int i=2;i<=n;i++){
            a[i]=(a[i-1]+a[i-2])%1000000007;
        }
        return a[n];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/qing-wa-tiao-tai-jie-wen-ti-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/qing-wa-tiao-tai-jie-wen-ti-lcof/)

[回到目录](../README.md)