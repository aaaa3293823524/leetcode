﻿# 剑指 Offer 16. shu-zhi-de-zheng-shu-ci-fang-lcof | 数值的整数次方

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>实现 <a href="https://www.cplusplus.com/reference/valarray/pow/">pow(<em>x</em>, <em>n</em>)</a> ，即计算 x 的 n 次幂函数（即，x<sup>n</sup>）。不得使用库函数，同时不需要考虑大数问题。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>x = 2.00000, n = 10
<strong>输出：</strong>1024.00000
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>x = 2.10000, n = 3
<strong>输出：</strong>9.26100</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>x = 2.00000, n = -2
<strong>输出：</strong>0.25000
<strong>解释：</strong>2<sup>-2</sup> = 1/2<sup>2</sup> = 1/4 = 0.25</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>-100.0 < x < 100.0</code></li>
	<li><code>-2<sup>31</sup> <= n <= 2<sup>31</sup>-1</code></li>
	<li><code>-10<sup>4</sup> <= x<sup>n</sup> <= 10<sup>4</sup></code></li>
</ul>

<p> </p>

<p>注意：本题与主站 50 题相同：<a href="https://leetcode-cn.com/problems/powx-n/">https://leetcode-cn.com/problems/powx-n/</a></p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public double myPow(double x, int n) {
        double ans=1;
        double cur_x=x;
        
        long t=n;
        if(n<0)t=-t;
        //if(n>0){
        while(t!=0){
            if(t%2==1)ans*=cur_x;
            cur_x*=cur_x;
            t/=2;
        }
        // }else{
        //     n=-n
        // }
        return n>0?ans:1/ans;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/shu-zhi-de-zheng-shu-ci-fang-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shu-zhi-de-zheng-shu-ci-fang-lcof/)

[回到目录](../README.md)