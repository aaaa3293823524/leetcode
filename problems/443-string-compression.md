﻿# 443. string-compression | 压缩字符串

## Question description

<!--If you want to use the English description, use <p>Given an array of characters <code>chars</code>, compress it using the following algorithm:</p>

<p>Begin with an empty string <code>s</code>. For each group of <strong>consecutive repeating characters</strong> in <code>chars</code>:</p>

<ul>
	<li>If the group&#39;s length is <code>1</code>, append the character to <code>s</code>.</li>
	<li>Otherwise, append the character followed by the group&#39;s length.</li>
</ul>

<p>The compressed string <code>s</code> <strong>should not be returned separately</strong>, but instead, be stored <strong>in the input character array <code>chars</code></strong>. Note that group lengths that are <code>10</code> or longer will be split into multiple characters in <code>chars</code>.</p>

<p>After you are done <strong>modifying the input array,</strong> return <em>the new length of the array</em>.</p>

<p>You must write an algorithm that uses only constant extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> chars = [&quot;a&quot;,&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;c&quot;,&quot;c&quot;,&quot;c&quot;]
<strong>Output:</strong> Return 6, and the first 6 characters of the input array should be: [&quot;a&quot;,&quot;2&quot;,&quot;b&quot;,&quot;2&quot;,&quot;c&quot;,&quot;3&quot;]
<strong>Explanation:</strong> The groups are &quot;aa&quot;, &quot;bb&quot;, and &quot;ccc&quot;. This compresses to &quot;a2b2c3&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> chars = [&quot;a&quot;]
<strong>Output:</strong> Return 1, and the first character of the input array should be: [&quot;a&quot;]
<strong>Explanation:</strong> The only group is &quot;a&quot;, which remains uncompressed since it&#39;s a single character.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> chars = [&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;]
<strong>Output:</strong> Return 4, and the first 4 characters of the input array should be: [&quot;a&quot;,&quot;b&quot;,&quot;1&quot;,&quot;2&quot;].
<strong>Explanation:</strong> The groups are &quot;a&quot; and &quot;bbbbbbbbbbbb&quot;. This compresses to &quot;ab12&quot;.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= chars.length &lt;= 2000</code></li>
	<li><code>chars[i]</code> is a lowercase English letter, uppercase English letter, digit, or symbol.</li>
</ul>
 instead-->
<p>给你一个字符数组 <code>chars</code> ，请使用下述算法压缩：</p>

<p>从一个空字符串 <code>s</code> 开始。对于 <code>chars</code> 中的每组 <strong>连续重复字符</strong> ：</p>

<ul>
	<li>如果这一组长度为 <code>1</code> ，则将字符追加到 <code>s</code> 中。</li>
	<li>否则，需要向 <code>s</code> 追加字符，后跟这一组的长度。</li>
</ul>

<p>压缩后得到的字符串 <code>s</code> <strong>不应该直接返回</strong> ，需要转储到字符数组 <code>chars</code> 中。需要注意的是，如果组长度为 <code>10</code> 或 <code>10</code> 以上，则在 <code>chars</code> 数组中会被拆分为多个字符。</p>

<p>请在 <strong>修改完输入数组后</strong> ，返回该数组的新长度。</p>

<p>你必须设计并实现一个只使用常量额外空间的算法来解决此问题。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>chars = ["a","a","b","b","c","c","c"]
<strong>输出：</strong>返回 6 ，输入数组的前 6 个字符应该是：["a","2","b","2","c","3"]
<strong>解释：</strong>
"aa" 被 "a2" 替代。"bb" 被 "b2" 替代。"ccc" 被 "c3" 替代。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>chars = ["a"]
<strong>输出：</strong>返回 1 ，输入数组的前 1 个字符应该是：["a"]
<strong>解释：</strong>
没有任何字符串被替代。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]
<strong>输出：</strong>返回 4 ，输入数组的前 4 个字符应该是：["a","b","1","2"]。
<strong>解释：</strong>
由于字符 "a" 不重复，所以不会被压缩。"bbbbbbbbbbbb" 被 “b12” 替代。
注意每个数字在数组中都有它自己的位置。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= chars.length &lt;= 2000</code></li>
	<li><code>chars[i]</code> 可以是小写英文字母、大写英文字母、数字或符号</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int compress(char[] chars) {
        int n = chars.length;
        int write = 0, left = 0;
        for (int read = 0; read < n; read++) {
            if (read == n - 1 || chars[read] != chars[read + 1]) {
                chars[write++] = chars[read];
                int num = read - left + 1;
                if (num > 1) {
                    int anchor = write;
                    while (num > 0) {
                        chars[write++] = (char) (num % 10 + '0');
                        num /= 10;
                    }
                    reverse(chars, anchor, write - 1);
                }
                left = read + 1;
            }
        }
        return write;
    }

    public void reverse(char[] chars, int left, int right) {
        while (left < right) {
            char temp = chars[left];
            chars[left] = chars[right];
            chars[right] = temp;
            left++;
            right--;
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/string-compression/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/string-compression/description/)

Solution: [LeetCode](https://leetcode.com/articles/string-compression/)  /  [LeetCode中国](https://leetcode-cn.com/articles/string-compression/)

[回到目录](../README.md)