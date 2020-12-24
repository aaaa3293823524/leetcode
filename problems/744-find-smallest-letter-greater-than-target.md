# 744. find-smallest-letter-greater-than-target | 寻找比目标字母大的最小字母

## Question description

<!--If you want to use the English description, use <p>
Given a list of sorted characters <code>letters</code> containing only lowercase letters, and given a target letter <code>target</code>, find the smallest element in the list that is larger than the given target.
</p><p>
Letters also wrap around.  For example, if the target is <code>target = 'z'</code> and <code>letters = ['a', 'b']</code>, the answer is <code>'a'</code>.
</p>

<p><b>Examples:</b><br />
<pre>
<b>Input:</b>
letters = ["c", "f", "j"]
target = "a"
<b>Output:</b> "c"

<b>Input:</b>
letters = ["c", "f", "j"]
target = "c"
<b>Output:</b> "f"

<b>Input:</b>
letters = ["c", "f", "j"]
target = "d"
<b>Output:</b> "f"

<b>Input:</b>
letters = ["c", "f", "j"]
target = "g"
<b>Output:</b> "j"

<b>Input:</b>
letters = ["c", "f", "j"]
target = "j"
<b>Output:</b> "c"

<b>Input:</b>
letters = ["c", "f", "j"]
target = "k"
<b>Output:</b> "c"
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li><code>letters</code> has a length in range <code>[2, 10000]</code>.</li>
<li><code>letters</code> consists of lowercase letters, and contains at least 2 unique letters.</li>
<li><code>target</code> is a lowercase letter.</li>
</ol>
</p> instead-->
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