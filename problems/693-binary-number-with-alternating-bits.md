# 693. binary-number-with-alternating-bits | 交替位二进制数

## Question description

<!--If you want to use the English description, use <p>Given a positive integer, check whether it has alternating bits: namely, if two adjacent bits will always have different values.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 5
<strong>Output:</strong> true
<strong>Explanation:</strong> The binary representation of 5 is: 101
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 7
<strong>Output:</strong> false
<strong>Explanation:</strong> The binary representation of 7 is: 111.</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 11
<strong>Output:</strong> false
<strong>Explanation:</strong> The binary representation of 11 is: 1011.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给定一个正整数，检查它的二进制表示是否总是 0、1 交替出现：换句话说，就是二进制表示中相邻两位的数字永不相同。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 5
<strong>输出：</strong>true
<strong>解释：</strong>5 的二进制表示是：101
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 7
<strong>输出：</strong>false
<strong>解释：</strong>7 的二进制表示是：111.</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>n = 11
<strong>输出：</strong>false
<strong>解释：</strong>11 的二进制表示是：1011.</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>n = 10
<strong>输出：</strong>true
<strong>解释：</strong>10 的二进制表示是：1010.</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>false
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= n <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 14 ms

```java
class Solution {
    public boolean hasAlternatingBits(int n) {
        int pre=-1;
        //List<Integer>list=new ArrayList<Integer>();
        while(n!=0){
            int g=n%2;
            System.out.println("g:"+g);
            System.out.println("pre:"+pre);
            System.out.println(g^pre);
            if((pre!=-1)&&((g^pre)==0)){
                return false;
            }
            pre=g;
            n/=2;
        }
        return true;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-number-with-alternating-bits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-number-with-alternating-bits/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-number-with-alternating-bits/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-number-with-alternating-bits/)

[回到目录](../README.md)