# 1945. sum-of-digits-of-string-after-convert | 字符串转化后的各位数字之和

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>s</code> consisting of lowercase English letters, and an integer <code>k</code>.</p>

<p>First, <strong>convert</strong> <code>s</code> into an integer by replacing each letter with its position in the alphabet (i.e., replace <code>&#39;a&#39;</code> with <code>1</code>, <code>&#39;b&#39;</code> with <code>2</code>, ..., <code>&#39;z&#39;</code> with <code>26</code>). Then, <strong>transform</strong> the integer by replacing it with the <strong>sum of its digits</strong>. Repeat the <strong>transform</strong> operation <code>k</code><strong> times</strong> in total.</p>

<p>For example, if <code>s = &quot;zbax&quot;</code> and <code>k = 2</code>, then the resulting integer would be <code>8</code> by the following operations:</p>

<ul>
	<li><strong>Convert</strong>: <code>&quot;zbax&quot; ➝ &quot;(26)(2)(1)(24)&quot; ➝ &quot;262124&quot; ➝ 262124</code></li>
	<li><strong>Transform #1</strong>: <code>262124 ➝ 2 + 6 + 2 + 1 + 2 + 4&nbsp;➝ 17</code></li>
	<li><strong>Transform #2</strong>: <code>17 ➝ 1 + 7 ➝ 8</code></li>
</ul>

<p>Return <em>the resulting integer after performing the operations described above</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;iiii&quot;, k = 1
<strong>Output:</strong> 36
<strong>Explanation:</strong> The operations are as follows:
- Convert: &quot;iiii&quot; ➝ &quot;(9)(9)(9)(9)&quot; ➝ &quot;9999&quot; ➝ 9999
- Transform #1: 9999 ➝ 9 + 9 + 9 + 9 ➝ 36
Thus the resulting integer is 36.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcode&quot;, k = 2
<strong>Output:</strong> 6
<strong>Explanation:</strong> The operations are as follows:
- Convert: &quot;leetcode&quot; ➝ &quot;(12)(5)(5)(20)(3)(15)(4)(5)&quot; ➝ &quot;12552031545&quot; ➝ 12552031545
- Transform #1: 12552031545 ➝ 1 + 2 + 5 + 5 + 2 + 0 + 3 + 1 + 5 + 4 + 5 ➝ 33
- Transform #2: 33 ➝ 3 + 3 ➝ 6
Thus the resulting integer is 6.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;zbax&quot;, k = 2
<strong>Output:</strong> 8
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>1 &lt;= k &lt;= 10</code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个由小写字母组成的字符串 <code>s</code> ，以及一个整数 <code>k</code> 。</p>

<p>首先，用字母在字母表中的位置替换该字母，将 <code>s</code> <strong>转化</strong> 为一个整数（也就是，<code>'a'</code> 用 <code>1</code> 替换，<code>'b'</code> 用 <code>2</code> 替换，... <code>'z'</code> 用 <code>26</code> 替换）。接着，将整数 <strong>转换</strong> 为其 <strong>各位数字之和</strong> 。共重复 <strong>转换</strong> 操作 <strong><code>k</code> 次</strong> 。</p>

<p>例如，如果 <code>s = "zbax"</code> 且 <code>k = 2</code> ，那么执行下述步骤后得到的结果是整数 <code>8</code> ：</p>

<ul>
	<li><strong>转化：</strong><code>"zbax" ➝ "(26)(2)(1)(24)" ➝ "262124" ➝ 262124</code></li>
	<li><strong>转换 #1</strong>：<code>262124&nbsp;➝ 2 + 6 + 2 + 1 + 2 + 4&nbsp;➝ 17</code></li>
	<li><strong>转换 #2</strong>：<code>17 ➝ 1 + 7 ➝ 8</code></li>
</ul>

<p>返回执行上述操作后得到的结果整数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "iiii", k = 1
<strong>输出：</strong>36
<strong>解释：</strong>操作如下：
- 转化："iiii" ➝ "(9)(9)(9)(9)" ➝ "9999" ➝ 9999
- 转换 #1：9999 ➝ 9 + 9 + 9 + 9 ➝ 36
因此，结果整数为 36 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "leetcode", k = 2
<strong>输出：</strong>6
<strong>解释：</strong>操作如下：
- 转化："leetcode" ➝ "(12)(5)(5)(20)(3)(15)(4)(5)" ➝ "12552031545" ➝ 12552031545
- 转换 #1：12552031545 ➝ 1 + 2 + 5 + 5 + 2 + 0 + 3 + 1 + 5 + 4 + 5 ➝ 33
- 转换 #2：33 ➝ 3 + 3 ➝ 6
因此，结果整数为 6 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>1 &lt;= k &lt;= 10</code></li>
	<li><code>s</code> 由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int getLucky(String s, int k) {
        StringBuilder stringBuilder=new StringBuilder();
        for(int i=0;i<s.length();i++) {
            stringBuilder.append(s.charAt(i)-'a'+1);
        }
        //Integer t=Integer.valueOf(stringBuilder.toString());
        String string=stringBuilder.toString();
        System.out.println(": "+string);
        
        for(int i=0;i<k;i++) {
            int sum=0;
            for(int j=0;j<string.length();j++) {
                sum+=Integer.valueOf(string.charAt(j)-'0');
            }
            System.out.println(sum);
            string=String.valueOf(sum);
        }
        return Integer.valueOf(string);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-digits-of-string-after-convert/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-digits-of-string-after-convert/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-digits-of-string-after-convert/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-digits-of-string-after-convert/)

[回到目录](../README.md)