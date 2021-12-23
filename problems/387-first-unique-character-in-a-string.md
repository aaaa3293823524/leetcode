# 387. first-unique-character-in-a-string | 字符串中的第一个唯一字符

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, <em>find the first non-repeating character in it and return its index</em>. If it does not exist, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "leetcode"
<strong>Output:</strong> 0
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "loveleetcode"
<strong>Output:</strong> 2
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = "aabb"
<strong>Output:</strong> -1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>
 instead-->
<p>给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre>s = &quot;leetcode&quot;
返回 0

s = &quot;loveleetcode&quot;
返回 2
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong>你可以假定该字符串只包含小写字母。</p>




## Solution

Language: **java**  /  Runtime: 18 ms

```java
class Solution {
    public int firstUniqChar(String s) {
        int len=s.length();
        int hashTable[]=new int[1010];
        for(int i=0;i<len;i++){
           hashTable[s.charAt(i)]++;
        }
        for(int i=0;i<len;i++){
           if(hashTable[s.charAt(i)]==1)return i;
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/first-unique-character-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/first-unique-character-in-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/first-unique-character-in-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/first-unique-character-in-a-string/)

[回到目录](../README.md)