# 1935. maximum-number-of-words-you-can-type | 可以输入的最大单词数

## Question description

<!--If you want to use the English description, use <p>There is a malfunctioning keyboard where some letter keys do not work. All other keys on the keyboard work properly.</p>

<p>Given a string <code>text</code> of words separated by a single space (no leading or trailing spaces) and a string <code>brokenLetters</code> of all <strong>distinct</strong> letter keys that are broken, return <em>the <strong>number of words</strong> in</em> <code>text</code> <em>you can fully type using this keyboard</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> text = &quot;hello world&quot;, brokenLetters = &quot;ad&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> We cannot type &quot;world&quot; because the &#39;d&#39; key is broken.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> text = &quot;leet code&quot;, brokenLetters = &quot;lt&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> We cannot type &quot;leet&quot; because the &#39;l&#39; and &#39;t&#39; keys are broken.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> text = &quot;leet code&quot;, brokenLetters = &quot;e&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> We cannot type either word because the &#39;e&#39; key is broken.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= text.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= brokenLetters.length &lt;= 26</code></li>
	<li><code>text</code> consists of words separated by a single space without any leading or trailing spaces.</li>
	<li>Each word only consists of lowercase English letters.</li>
	<li><code>brokenLetters</code> consists of <strong>distinct</strong> lowercase English letters.</li>
</ul>
 instead-->
<p>键盘出现了一些故障，有些字母键无法正常工作。而键盘上所有其他键都能够正常工作。</p>

<p>给你一个由若干单词组成的字符串 <code>text</code> ，单词间由单个空格组成（不含前导和尾随空格）；另有一个字符串 <code>brokenLetters</code> ，由所有已损坏的不同字母键组成，返回你可以使用此键盘完全输入的 <code>text</code> 中单词的数目。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>text = "hello world", brokenLetters = "ad"
<strong>输出：</strong>1
<strong>解释：</strong>无法输入 "world" ，因为字母键 'd' 已损坏。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>text = "leet code", brokenLetters = "lt"
<strong>输出：</strong>1
<strong>解释：</strong>无法输入 "leet" ，因为字母键 'l' 和 't' 已损坏。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>text = "leet code", brokenLetters = "e"
<strong>输出：</strong>0
<strong>解释：</strong>无法输入任何单词，因为字母键 'e' 已损坏。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= text.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= brokenLetters.length &lt;= 26</code></li>
	<li><code>text</code> 由若干用单个空格分隔的单词组成，且不含任何前导和尾随空格</li>
	<li>每个单词仅由小写英文字母组成</li>
	<li><code>brokenLetters</code> 由 <strong>互不相同</strong> 的小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int canBeTypedWords(String text, String brokenLetters) {
        String[]strings=text.split(" ");
        char[]c=brokenLetters.toCharArray();
        HashMap<Character, Integer>map=new HashMap<Character, Integer>();
        for(int i=0;i<c.length;i++) {
            map.put(c[i], map.getOrDefault(c[i],0)+1);
        }
        int count=0;
        for(int i=0;i<strings.length;i++) {
            strings[i].length();
            boolean flag=true;
            for(int j=0;j<strings[i].length();j++) {
                if(map.containsKey(strings[i].charAt(j))) {
                    flag=false;
                    break;
                }
            }
            if(flag)count++;
        }
        return count;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-number-of-words-you-can-type/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-number-of-words-you-can-type/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-number-of-words-you-can-type/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-number-of-words-you-can-type/)

[回到目录](../README.md)