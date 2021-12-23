# 3. longest-substring-without-repeating-characters | 无重复字符的最长子串

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, find the length of the <strong>longest substring</strong> without repeating characters.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcabcbb&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is &quot;abc&quot;, with the length of 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bbbbb&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> The answer is &quot;b&quot;, with the length of 1.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;pwwkew&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is &quot;wke&quot;, with the length of 3.
Notice that the answer must be a substring, &quot;pwke&quot; is a subsequence and not a substring.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> consists of English letters, digits, symbols and spaces.</li>
</ul>
 instead-->
<p>给定一个字符串 <code>s</code> ，请你找出其中不含有重复字符的 <strong>最长子串 </strong>的长度。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入: </strong>s = "abcabcbb"
<strong>输出: </strong>3 
<strong>解释:</strong> 因为无重复字符的最长子串是 <code>"abc"，所以其</code>长度为 3。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入: </strong>s = "bbbbb"
<strong>输出: </strong>1
<strong>解释: </strong>因为无重复字符的最长子串是 <code>"b"</code>，所以其长度为 1。
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入: </strong>s = "pwwkew"
<strong>输出: </strong>3
<strong>解释: </strong>因为无重复字符的最长子串是 <code>"wke"</code>，所以其长度为 3。
     请注意，你的答案必须是 <strong>子串 </strong>的长度，<code>"pwke"</code> 是一个<em>子序列，</em>不是子串。
</pre>

<p><strong>示例 4:</strong></p>

<pre>
<strong>输入: </strong>s = ""
<strong>输出: </strong>0
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= s.length <= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> 由英文字母、数字、符号和空格组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int ans=0;
        char[]c=s.toCharArray();
        int rk=0;
        HashMap<Character, Integer>map=new HashMap<Character, Integer>();
        for(int i=0;i<c.length;i++) {
            if(i!=0) {
                map.remove(c[i-1]);
            }
            while(rk<c.length&&!map.containsKey(c[rk])){
                map.put(c[rk],1);
                rk++;
            }
            ans=Math.max(rk-i, ans);
        }
        return ans;
    }
    // public int lengthOfLongestSubstring(String s) {
    //     HashMap<Character, Integer>map=new HashMap<Character, Integer>();
    //     int rk=-1;
    //     int ans=0;
    //     for(int i=0;i<s.length();i++) {
    //         //int len=0;
    //         if(i!=0) {
    //             map.remove(s.charAt(i-1));
    //         }
            
    //         while(rk+1<s.length()&&!map.containsKey(s.charAt(rk+1))) {
                
    //             map.put(s.charAt(rk+1), 1);
    //             rk++;
    //         }
    //         ans=Math.max(ans, rk-i+1);
    //     }
    //     return ans;
    // }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-substring-without-repeating-characters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-substring-without-repeating-characters/)

[回到目录](../README.md)