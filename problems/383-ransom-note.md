# 383. ransom-note | 赎金信

## Question description

<!--If you want to use the English description, use <p>Given two stings <code>ransomNote</code> and <code>magazine</code>, return <code>true</code> if <code>ransomNote</code> can be constructed from <code>magazine</code> and <code>false</code> otherwise.</p>

<p>Each letter in <code>magazine</code> can only be used once in <code>ransomNote</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> ransomNote = "a", magazine = "b"
<strong>Output:</strong> false
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> ransomNote = "aa", magazine = "ab"
<strong>Output:</strong> false
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> ransomNote = "aa", magazine = "aab"
<strong>Output:</strong> true
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= ransomNote.length, magazine.length &lt;= 10<sup>5</sup></code></li>
	<li><code>ransomNote</code> and <code>magazine</code> consist of lowercase English letters.</li>
</ul>
 instead-->
<p>给你两个字符串：<code>ransomNote</code> 和 <code>magazine</code> ，判断 <code>ransomNote</code> 能不能由 <code>magazine</code> 里面的字符构成。</p>

<p>如果可以，返回 <code>true</code> ；否则返回 <code>false</code> 。</p>

<p><code>magazine</code> 中的每个字符只能在 <code>ransomNote</code> 中使用一次。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>ransomNote = "a", magazine = "b"
<strong>输出：</strong>false
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>ransomNote = "aa", magazine = "ab"
<strong>输出：</strong>false
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>ransomNote = "aa", magazine = "aab"
<strong>输出：</strong>true
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= ransomNote.length, magazine.length &lt;= 10<sup>5</sup></code></li>
	<li><code>ransomNote</code> 和 <code>magazine</code> 由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        // 新建小写字母频次统计数组，0-25 分别代表 a-z
        int[] charCountRN = new int[26];
        int[] charCountM = new int[26];
        // 将 String 转化成 char[] 可以加速程序，因为 String.charAt() 每次调用都会检查下标是否越界
        char[] charArrayRN = ransomNote.toCharArray();
        char[] charArrayM = magazine.toCharArray();
        // 统计救赎信的各个字母出现次数
        for (char c : charArrayRN) {
            charCountRN[c-'a']++;
        }
        // 统计杂志的各个字母出现次数
        for (char c : charArrayM) {
            charCountM[c-'a']++;
        }
        // 对每个字母的出现次数进行比较
        for (int i = 0; i < 26; i++) {
            if(charCountRN[i] > charCountM[i]){
                return false;
            }
        }
        return true;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ransom-note/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ransom-note/description/)

Solution: [LeetCode](https://leetcode.com/articles/ransom-note/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ransom-note/)

[回到目录](../README.md)