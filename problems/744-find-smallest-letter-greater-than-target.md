# 744. find-smallest-letter-greater-than-target | 寻找比目标字母大的最小字母

## Question description

<!--If you want to use the English description, use <p>Given a characters array <code>letters</code> that is sorted in <strong>non-decreasing</strong> order and a character <code>target</code>, return <em>the smallest character in the array that is larger than </em><code>target</code>.</p>

<p><strong>Note</strong> that the letters wrap around.</p>

<ul>
	<li>For example, if <code>target == &#39;z&#39;</code> and <code>letters == [&#39;a&#39;, &#39;b&#39;]</code>, the answer is <code>&#39;a&#39;</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> letters = [&quot;c&quot;,&quot;f&quot;,&quot;j&quot;], target = &quot;a&quot;
<strong>Output:</strong> &quot;c&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> letters = [&quot;c&quot;,&quot;f&quot;,&quot;j&quot;], target = &quot;c&quot;
<strong>Output:</strong> &quot;f&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> letters = [&quot;c&quot;,&quot;f&quot;,&quot;j&quot;], target = &quot;d&quot;
<strong>Output:</strong> &quot;f&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= letters.length &lt;= 10<sup>4</sup></code></li>
	<li><code>letters[i]</code> is a lowercase English letter.</li>
	<li><code>letters</code> is sorted in <strong>non-decreasing</strong> order.</li>
	<li><code>letters</code> contains at least two different characters.</li>
	<li><code>target</code> is a lowercase English letter.</li>
</ul>
 instead-->
<p>给你一个排序后的字符列表 <code>letters</code> ，列表中只包含小写英文字母。另给出一个目标字母&nbsp;<code>target</code>，请你寻找在这一有序列表里比目标字母大的最小字母。</p>

<p>在比较时，字母是依序循环出现的。举个例子：</p>

<ul>
	<li>如果目标字母 <code>target = &#39;z&#39;</code> 并且字符列表为&nbsp;<code>letters = [&#39;a&#39;, &#39;b&#39;]</code>，则答案返回&nbsp;<code>&#39;a&#39;</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入:</strong>
letters = [&quot;c&quot;, &quot;f&quot;, &quot;j&quot;]
target = &quot;a&quot;
<strong>输出:</strong> &quot;c&quot;

<strong>输入:</strong>
letters = [&quot;c&quot;, &quot;f&quot;, &quot;j&quot;]
target = &quot;c&quot;
<strong>输出:</strong> &quot;f&quot;

<strong>输入:</strong>
letters = [&quot;c&quot;, &quot;f&quot;, &quot;j&quot;]
target = &quot;d&quot;
<strong>输出:</strong> &quot;f&quot;

<strong>输入:</strong>
letters = [&quot;c&quot;, &quot;f&quot;, &quot;j&quot;]
target = &quot;g&quot;
<strong>输出:</strong> &quot;j&quot;

<strong>输入:</strong>
letters = [&quot;c&quot;, &quot;f&quot;, &quot;j&quot;]
target = &quot;j&quot;
<strong>输出:</strong> &quot;c&quot;

<strong>输入:</strong>
letters = [&quot;c&quot;, &quot;f&quot;, &quot;j&quot;]
target = &quot;k&quot;
<strong>输出:</strong> &quot;c&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>letters</code>长度范围在<code>[2, 10000]</code>区间内。</li>
	<li><code>letters</code> 仅由小写字母组成，最少包含两个不同的字母。</li>
	<li>目标字母<code>target</code> 是一个小写字母。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public static char nextGreatestLetter(char[] letters, char target) {
        if (letters[0] > target || letters[letters.length - 1] <= target)
            return letters[0];
        int left = 1, right = letters.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (letters[mid] <= target)
                left = mid + 1;
            else {
                if (letters[mid - 1] <= target)
                    return letters[mid];
                else right = mid - 1;
            }
        }
        return ' ';
    }

}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-smallest-letter-greater-than-target/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-smallest-letter-greater-than-target/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-smallest-letter-greater-than-target/)

[回到目录](../README.md)