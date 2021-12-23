# 剑指 Offer 65. bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof | 不用加减乘除做加法

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>写一个函数，求两个整数之和，要求在函数体内不得使用 &ldquo;+&rdquo;、&ldquo;-&rdquo;、&ldquo;*&rdquo;、&ldquo;/&rdquo; 四则运算符号。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> a = 1, b = 1
<strong>输出:</strong> 2</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>a</code>,&nbsp;<code>b</code>&nbsp;均可能是负数或 0</li>
	<li>结果不会溢出 32 位整数</li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int add(int a, int b) {
        while(b != 0) { // 当进位为 0 时跳出
            int c = (a & b) << 1;  // c = 进位
            a ^= b; // a = 非进位和
            b = c; // b = 进位
        }
        return a;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

[回到目录](../README.md)