# 剑指 Offer 10- I. fei-bo-na-qi-shu-lie-lcof | 斐波那契数列

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>写一个函数，输入 <code>n</code> ，求斐波那契（Fibonacci）数列的第 <code>n</code> 项（即 <code>F(N)</code>）。斐波那契数列的定义如下：</p>

<pre>
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.</pre>

<p>斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。</p>

<p>答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 2
<strong>输出：</strong>1
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 5
<strong>输出：</strong>5
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= n <= 100</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int fib(int n) {
        int[] a=new int[101];
        a[0]=0;a[1]=1;
        for(int i=2;i<=n;i++){
            a[i]=(a[i-1]+a[i-2])%1000000007;
        }
        return a[n];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/fei-bo-na-qi-shu-lie-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/fei-bo-na-qi-shu-lie-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/fei-bo-na-qi-shu-lie-lcof/)

[回到目录](../README.md)