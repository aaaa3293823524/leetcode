# 476. number-complement | 数字的补数

## Question description

<!--If you want to use the English description, use <p>The <strong>complement</strong> of an integer is the integer you get when you flip all the <code>0</code>&#39;s to <code>1</code>&#39;s and all the <code>1</code>&#39;s to <code>0</code>&#39;s in its binary representation.</p>

<ul>
	<li>For example, The integer <code>5</code> is <code>&quot;101&quot;</code> in binary and its <strong>complement</strong> is <code>&quot;010&quot;</code> which is the integer <code>2</code>.</li>
</ul>

<p>Given an integer <code>num</code>, return <em>its complement</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 5
<strong>Output:</strong> 2
<strong>Explanation:</strong> The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 1
<strong>Output:</strong> 0
<strong>Explanation:</strong> The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num &lt; 2<sup>31</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Note:</strong> This question is the same as 1009: <a href="https://leetcode.com/problems/complement-of-base-10-integer/" target="_blank">https://leetcode.com/problems/complement-of-base-10-integer/</a></p>
 instead-->
<p>对整数的二进制表示取反（<code>0</code> 变 <code>1</code> ，<code>1</code> 变 <code>0</code>）后，再转换为十进制表示，可以得到这个整数的补数。</p>

<ul>
	<li>例如，整数 <code>5</code> 的二进制表示是 <code>"101"</code> ，取反后得到 <code>"010"</code> ，再转回十进制表示得到补数 <code>2</code> 。</li>
</ul>

<p>给你一个整数 <code>num</code> ，输出它的补数。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>num = 5
<strong>输出：</strong>2
<strong>解释：</strong>5 的二进制表示为 101（没有前导零位），其补数为 010。所以你需要输出 2 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>num = 1
<strong>输出：</strong>0
<strong>解释：</strong>1 的二进制表示为 1（没有前导零位），其补数为 0。所以你需要输出 0 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num &lt; 2<sup>31</sup></code></li>
</ul>

<p>&nbsp;</p>

<p><strong>注意：</strong>本题与 1009 <a href="https://leetcode-cn.com/problems/complement-of-base-10-integer/">https://leetcode-cn.com/problems/complement-of-base-10-integer/</a> 相同</p>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int findComplement(int num) {
        String s=Integer.toBinaryString(num);
        int res=0;
        int temp=0;
        int r=s.length()-1;
        while(r>=0){
           if(s.charAt(r) == '0') res += Math.pow(2,temp);
           temp ++;
           r--;
        }
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-complement/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-complement/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-complement/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-complement/)

[回到目录](../README.md)