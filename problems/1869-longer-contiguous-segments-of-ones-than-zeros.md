# 1869. longer-contiguous-segments-of-ones-than-zeros | 哪种连续子字符串更长

## Question description

<!--If you want to use the English description, use <p>Given a binary string <code>s</code>, return <code>true</code><em> if the <strong>longest</strong> contiguous segment of </em><code>1</code>&#39;<em>s is <strong>strictly longer</strong> than the <strong>longest</strong> contiguous segment of </em><code>0</code>&#39;<em>s in </em><code>s</code>, or return <code>false</code><em> otherwise</em>.</p>

<ul>
	<li>For example, in <code>s = &quot;<u>11</u>01<u>000</u>10&quot;</code> the longest continuous segment of <code>1</code>s has length <code>2</code>, and the longest continuous segment of <code>0</code>s has length <code>3</code>.</li>
</ul>

<p>Note that if there are no <code>0</code>&#39;s, then the longest continuous segment of <code>0</code>&#39;s is considered to have a length <code>0</code>. The same applies if there is no <code>1</code>&#39;s.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1101&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong>
The longest contiguous segment of 1s has length 2: &quot;<u>11</u>01&quot;
The longest contiguous segment of 0s has length 1: &quot;11<u>0</u>1&quot;
The segment of 1s is longer, so return true.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;111000&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong>
The longest contiguous segment of 1s has length 3: &quot;<u>111</u>000&quot;
The longest contiguous segment of 0s has length 3: &quot;111<u>000</u>&quot;
The segment of 1s is not longer, so return false.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;110100010&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong>
The longest contiguous segment of 1s has length 2: &quot;<u>11</u>0100010&quot;
The longest contiguous segment of 0s has length 3: &quot;1101<u>000</u>10&quot;
The segment of 1s is not longer, so return false.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s[i]</code> is either <code>&#39;0&#39;</code> or <code>&#39;1&#39;</code>.</li>
</ul>
 instead-->
<p>给你一个二进制字符串 <code>s</code> 。如果字符串中由 <code>1</code> 组成的 <strong>最长</strong> 连续子字符串 <strong>严格长于</strong> 由 <code>0</code> 组成的 <strong>最长</strong> 连续子字符串，返回 <code>true</code> ；否则，返回 <code>false</code><em> </em>。</p>

<ul>
	<li>例如，<code>s = "<strong>11</strong>01<strong>000</strong>10"</code> 中，由 <code>1</code> 组成的最长连续子字符串的长度是 <code>2</code> ，由 <code>0</code> 组成的最长连续子字符串的长度是 <code>3</code> 。</li>
</ul>

<p>注意，如果字符串中不存在 <code>0</code> ，此时认为由 <code>0</code> 组成的最长连续子字符串的长度是 <code>0</code> 。字符串中不存在 <code>1</code> 的情况也适用此规则。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "1101"
<strong>输出：</strong>true
<strong>解释：</strong>
由 <code>1</code> 组成的最长连续子字符串的长度是 2："<strong>11</strong>01"
由 <code>0</code> 组成的最长连续子字符串的长度是 1："11<strong>0</strong>1"
由 1 组成的子字符串更长，故返回 true 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "111000"
<strong>输出：</strong>false
<strong>解释：</strong>
由 <code>1</code> 组成的最长连续子字符串的长度是 3："<strong>111</strong>000"
由<code> 0</code> 组成的最长连续子字符串的长度是 3："111<strong>000</strong>"
由 1 组成的子字符串不比由 0 组成的子字符串长，故返回 false 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "110100010"
<strong>输出：</strong>false
<strong>解释：</strong>
由 <code>1</code> 组成的最长连续子字符串的长度是 2："<strong>11</strong>0100010"
由 <code>0</code> 组成的最长连续子字符串的长度是 3："1101<strong>000</strong>10"
由 1 组成的子字符串不比由 0 组成的子字符串长，故返回 false 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 100</code></li>
	<li><code>s[i]</code> 不是 <code>'0'</code> 就是 <code>'1'</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public boolean checkZeroOnes(String s) {
        int zeros=0,ones=0;
        char[]c=s.toCharArray();
        char pre='-';
        int curZero=0,curOne=0;
        for(int i=0;i<s.length();i++) {
            
            if(c[i]=='0') {
                if(pre=='0') {
                    curZero++;
                    
                }else{
                    curZero=1;
                }
                pre='0';
                curOne=0;
            }
            if(c[i]=='1') {
                if(pre=='1') {
                    curOne++;
                    
                }else{
                    curOne=1;
                }
                pre='1';
                curZero=0;
            }
            zeros=Math.max(zeros, curZero);
            ones=Math.max(ones, curOne);
        }
        return ones>zeros?true:false;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longer-contiguous-segments-of-ones-than-zeros/description/)

Solution: [LeetCode](https://leetcode.com/articles/longer-contiguous-segments-of-ones-than-zeros/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longer-contiguous-segments-of-ones-than-zeros/)

[回到目录](../README.md)