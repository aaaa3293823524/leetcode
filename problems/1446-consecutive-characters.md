# 1446. consecutive-characters | 连续字符

## Question description

<!--If you want to use the English description, use <p>The <strong>power</strong> of the string is the maximum length of a non-empty substring that contains only one unique character.</p>

<p>Given a string <code>s</code>, return <em>the <strong>power</strong> of</em> <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcode&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The substring &quot;ee&quot; is of length 2 with the character &#39;e&#39; only.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abbcccddddeeeeedcba&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The substring &quot;eeeee&quot; is of length 5 with the character &#39;e&#39; only.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 500</code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个字符串&nbsp;<code>s</code>&nbsp;，字符串的「能量」定义为：只包含一种字符的最长非空子字符串的长度。</p>

<p>请你返回字符串的能量。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;leetcode&quot;
<strong>输出：</strong>2
<strong>解释：</strong>子字符串 &quot;ee&quot; 长度为 2 ，只包含字符 &#39;e&#39; 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;abbcccddddeeeeedcba&quot;
<strong>输出：</strong>5
<strong>解释：</strong>子字符串 &quot;eeeee&quot; 长度为 5 ，只包含字符 &#39;e&#39; 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;triplepillooooow&quot;
<strong>输出：</strong>5
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>s = &quot;hooraaaaaaaaaaay&quot;
<strong>输出：</strong>11
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：</strong>s = &quot;tourist&quot;
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 500</code></li>
	<li><code>s</code>&nbsp;只包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int maxPower(String s) {
        int ans=1;
        if(s==null||s.length()==0)return ans;
        for(int i=0;i<s.length();i++){
            int curLen=1;
            int j=i+1;
            while(j<s.length()&&s.charAt(j-1)==s.charAt(j)){
                curLen++;
                j++;
            }
            i=j-1;
            ans=Math.max(ans,curLen);
        }
        return ans;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/consecutive-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/consecutive-characters/description/)

Solution: [LeetCode](https://leetcode.com/articles/consecutive-characters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/consecutive-characters/)

[回到目录](../README.md)