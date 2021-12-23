# 461. hamming-distance | 汉明距离

## Question description

<!--If you want to use the English description, use <p>The <a href="https://en.wikipedia.org/wiki/Hamming_distance" target="_blank">Hamming distance</a> between two integers is the number of positions at which the corresponding bits are different.</p>

<p>Given two integers <code>x</code> and <code>y</code>, return <em>the <strong>Hamming distance</strong> between them</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> x = 1, y = 4
<strong>Output:</strong> 2
<strong>Explanation:</strong>
1   (0 0 0 1)
4   (0 1 0 0)
       &uarr;   &uarr;
The above arrows point to positions where the corresponding bits are different.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> x = 3, y = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;=&nbsp;x, y &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>两个整数之间的 <a href="https://baike.baidu.com/item/%E6%B1%89%E6%98%8E%E8%B7%9D%E7%A6%BB">汉明距离</a> 指的是这两个数字对应二进制位不同的位置的数目。</p>

<p>给你两个整数 <code>x</code> 和 <code>y</code>，计算并返回它们之间的汉明距离。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>x = 1, y = 4
<strong>输出：</strong>2
<strong>解释：</strong>
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑
上面的箭头指出了对应二进制位不同的位置。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>x = 3, y = 1
<strong>输出：</strong>1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= x, y <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int hammingDistance(int x, int y) {
        int t=x^y;
        int sum=0;
        for(int i=0;i<32;i++) {
            sum+=(t>>i)&1;
        }
        return sum;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/hamming-distance/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/hamming-distance/description/)

Solution: [LeetCode](https://leetcode.com/articles/hamming-distance/)  /  [LeetCode中国](https://leetcode-cn.com/articles/hamming-distance/)

[回到目录](../README.md)