# 696. count-binary-substrings | 计数二进制子串

## Question description

<!--If you want to use the English description, use <p>Give a binary string <code>s</code>, return the number of non-empty substrings that have the same number of <code>0</code>&#39;s and <code>1</code>&#39;s, and all the <code>0</code>&#39;s and all the <code>1</code>&#39;s in these substrings are grouped consecutively.</p>

<p>Substrings that occur multiple times are counted the number of times they occur.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;00110011&quot;
<strong>Output:</strong> 6
<strong>Explanation:</strong> There are 6 substrings that have equal number of consecutive 1&#39;s and 0&#39;s: &quot;0011&quot;, &quot;01&quot;, &quot;1100&quot;, &quot;10&quot;, &quot;0011&quot;, and &quot;01&quot;.
Notice that some of these substrings repeat and are counted the number of times they occur.
Also, &quot;00110011&quot; is not a valid substring because all the 0&#39;s (and 1&#39;s) are not grouped together.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;10101&quot;
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 substrings: &quot;10&quot;, &quot;01&quot;, &quot;10&quot;, &quot;01&quot; that have equal number of consecutive 1&#39;s and 0&#39;s.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is either <code>&#39;0&#39;</code> or <code>&#39;1&#39;</code>.</li>
</ul>
 instead-->
<p>给定一个字符串&nbsp;<code>s</code>，统计并返回具有相同数量 <code>0</code> 和 <code>1</code> 的非空（连续）子字符串的数量，并且这些子字符串中的所有 <code>0</code> 和所有 <code>1</code> 都是成组连续的。</p>

<p>重复出现（不同位置）的子串也要统计它们出现的次数。</p>
&nbsp;

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "00110011"
<strong>输出：</strong>6
<strong>解释：</strong>6 个子串满足具有相同数量的连续 1 和 0 ："0011"、"01"、"1100"、"10"、"0011" 和 "01" 。
注意，一些重复出现的子串（不同位置）要统计它们出现的次数。
另外，"00110011" 不是有效的子串，因为所有的 0（还有 1 ）没有组合在一起。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "10101"
<strong>输出：</strong>4
<strong>解释：</strong>有 4 个子串："10"、"01"、"10"、"01" ，具有相同数量的连续 1 和 0 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> 为 <code>'0'</code> 或 <code>'1'</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 12 ms

```java
class Solution {
    public int countBinarySubstrings(String s) {
        List<Integer> counts = new ArrayList<Integer>();
        int ptr = 0, n = s.length();
        while (ptr < n) {
            char c = s.charAt(ptr);
            int count = 0;
            while (ptr < n && s.charAt(ptr) == c) {
                ++ptr;
                ++count;
            }
            counts.add(count);
        }
        int ans = 0;
        for (int i = 1; i < counts.size(); ++i) {
            ans += Math.min(counts.get(i), counts.get(i - 1));
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/count-binary-substrings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-binary-substrings/description/)

Solution: [LeetCode](https://leetcode.com/articles/count-binary-substrings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/count-binary-substrings/)

[回到目录](../README.md)