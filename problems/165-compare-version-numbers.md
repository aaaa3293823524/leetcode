# 165. compare-version-numbers | 比较版本号

## Question description

<!--If you want to use the English description, use <p>Given two version numbers,&nbsp;<code>version1</code> and <code>version2</code>, compare them.</p>

<ul>
</ul>

<p>Version numbers consist of <strong>one or more revisions</strong> joined by a dot&nbsp;<code>&#39;.&#39;</code>. Each revision&nbsp;consists of <strong>digits</strong>&nbsp;and may contain leading <strong>zeros</strong>. Every revision contains <strong>at least one character</strong>. Revisions are <strong>0-indexed from left to right</strong>, with the leftmost revision being revision 0, the next revision being revision 1, and so on. For example&nbsp;<code>2.5.33</code>&nbsp;and&nbsp;<code>0.1</code>&nbsp;are valid version numbers.</p>

<p>To compare version numbers, compare their revisions in <strong>left-to-right order</strong>. Revisions are compared using their&nbsp;<strong>integer value ignoring any leading zeros</strong>. This means that revisions&nbsp;<code>1</code>&nbsp;and&nbsp;<code>001</code>&nbsp;are considered&nbsp;<strong>equal</strong>. If a version number does not specify a revision at an index, then&nbsp;<strong>treat the revision as&nbsp;<code>0</code></strong>. For example, version&nbsp;<code>1.0</code> is less than version&nbsp;<code>1.1</code>&nbsp;because their revision 0s are the same, but their revision 1s are&nbsp;<code>0</code>&nbsp;and&nbsp;<code>1</code>&nbsp;respectively, and&nbsp;<code>0 &lt; 1</code>.</p>

<p><em>Return the following:</em></p>

<ul>
	<li>If <code>version1 &lt; version2</code>, return <code>-1</code>.</li>
	<li>If <code>version1 &gt; version2</code>, return <code>1</code>.</li>
	<li>Otherwise, return <code>0</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> version1 = &quot;1.01&quot;, version2 = &quot;1.001&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> Ignoring leading zeroes, both &quot;01&quot; and &quot;001&quot; represent the same integer &quot;1&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> version1 = &quot;1.0&quot;, version2 = &quot;1.0.0&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> version1 does not specify revision 2, which means it is treated as &quot;0&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> version1 = &quot;0.1&quot;, version2 = &quot;1.1&quot;
<strong>Output:</strong> -1
<strong>Explanation:</strong> version1&#39;s revision 0 is &quot;0&quot;, while version2&#39;s revision 0 is &quot;1&quot;. 0 &lt; 1, so version1 &lt; version2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= version1.length, version2.length &lt;= 500</code></li>
	<li><code>version1</code> and <code>version2</code>&nbsp;only contain digits and <code>&#39;.&#39;</code>.</li>
	<li><code>version1</code> and <code>version2</code>&nbsp;<strong>are valid version numbers</strong>.</li>
	<li>All the given revisions in&nbsp;<code>version1</code> and <code>version2</code>&nbsp;can be stored in&nbsp;a&nbsp;<strong>32-bit integer</strong>.</li>
</ul>
 instead-->
<p>给你两个版本号 <code>version1</code> 和 <code>version2</code> ，请你比较它们。</p>

<p>版本号由一个或多个修订号组成，各修订号由一个 <code>'.'</code> 连接。每个修订号由 <strong>多位数字</strong> 组成，可能包含 <strong>前导零</strong> 。每个版本号至少包含一个字符。修订号从左到右编号，下标从 0 开始，最左边的修订号下标为 0 ，下一个修订号下标为 1 ，以此类推。例如，<code>2.5.33</code> 和 <code>0.1</code> 都是有效的版本号。</p>

<p>比较版本号时，请按从左到右的顺序依次比较它们的修订号。比较修订号时，只需比较 <strong>忽略任何前导零后的整数值</strong> 。也就是说，修订号 <code>1</code> 和修订号 <code>001</code> <strong>相等 </strong>。如果版本号没有指定某个下标处的修订号，则该修订号视为 <code>0</code> 。例如，版本 <code>1.0</code> 小于版本 <code>1.1</code> ，因为它们下标为 <code>0</code> 的修订号相同，而下标为 <code>1</code> 的修订号分别为 <code>0</code> 和 <code>1</code> ，<code>0 < 1</code> 。</p>

<p>返回规则如下：</p>

<ul>
	<li>如果 <code><em>version1 </em>> <em>version2</em></code> 返回 <code>1</code>，</li>
	<li>如果 <code><em>version1 </em>< <em>version2</em></code> 返回 <code>-1</code>，</li>
	<li>除此之外返回 <code>0</code>。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>version1 = "1.01", version2 = "1.001"
<strong>输出：</strong>0
<strong>解释：</strong>忽略前导零，"01" 和 "001" 都表示相同的整数 "1"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>version1 = "1.0", version2 = "1.0.0"
<strong>输出：</strong>0
<strong>解释：</strong>version1 没有指定下标为 2 的修订号，即视为 "0"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>version1 = "0.1", version2 = "1.1"
<strong>输出：</strong>-1
<strong>解释：</strong>version1 中下标为 0 的修订号是 "0"，version2 中下标为 0 的修订号是 "1" 。0 < 1，所以 version1 < version2
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>version1 = "1.0.1", version2 = "1"
<strong>输出：</strong>1
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>version1 = "7.5.2.4", version2 = "7.5.3"
<strong>输出：</strong>-1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= version1.length, version2.length <= 500</code></li>
	<li><code>version1</code> 和 <code>version2</code> 仅包含数字和 <code>'.'</code></li>
	<li><code>version1</code> 和 <code>version2</code> 都是 <strong>有效版本号</strong></li>
	<li><code>version1</code> 和 <code>version2</code> 的所有修订号都可以存储在 <strong>32 位整数</strong> 中</li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int compareVersion(String version1, String version2) {
        int n = version1.length(), m = version2.length();
        int i = 0, j = 0;
        while (i < n || j < m) {
            int x = 0;
            for (; i < n && version1.charAt(i) != '.'; ++i) {
                x = x * 10 + version1.charAt(i) - '0';
            }
            ++i; // 跳过点号
            int y = 0;
            for (; j < m && version2.charAt(j) != '.'; ++j) {
                y = y * 10 + version2.charAt(j) - '0';
            }
            ++j; // 跳过点号
            if (x != y) {
                return x > y ? 1 : -1;
            }
        }
        return 0;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/compare-version-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/compare-version-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/compare-version-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/compare-version-numbers/)

[回到目录](../README.md)