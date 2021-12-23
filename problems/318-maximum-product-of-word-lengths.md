# 318. maximum-product-of-word-lengths | 最大单词长度乘积

## Question description

<!--If you want to use the English description, use <p>Given a string array <code>words</code>, return <em>the maximum value of</em> <code>length(word[i]) * length(word[j])</code> <em>where the two words do not share common letters</em>. If no such two words exist, return <code>0</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;abcw&quot;,&quot;baz&quot;,&quot;foo&quot;,&quot;bar&quot;,&quot;xtfn&quot;,&quot;abcdef&quot;]
<strong>Output:</strong> 16
<strong>Explanation:</strong> The two words can be &quot;abcw&quot;, &quot;xtfn&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;a&quot;,&quot;ab&quot;,&quot;abc&quot;,&quot;d&quot;,&quot;cd&quot;,&quot;bcd&quot;,&quot;abcd&quot;]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The two words can be &quot;ab&quot;, &quot;cd&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;a&quot;,&quot;aa&quot;,&quot;aaa&quot;,&quot;aaaa&quot;]
<strong>Output:</strong> 0
<strong>Explanation:</strong> No such pair of words.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= words.length &lt;= 1000</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 1000</code></li>
	<li><code>words[i]</code> consists only of lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个字符串数组&nbsp;<code>words</code> ，找出并返回 <code>length(words[i]) * length(words[j])</code>&nbsp;的最大值，并且这两个单词不含有公共字母。如果不存在这样的两个单词，返回 <code>0</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1：</strong></p>

<pre>
<strong>输入：</strong>words = <code>["abcw","baz","foo","bar","xtfn","abcdef"]</code>
<strong>输出：</strong><code>16 
<strong>解释</strong></code><strong>：</strong><code>这两个单词为<strong> </strong>"abcw", "xtfn"</code>。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>words = <code>["a","ab","abc","d","cd","bcd","abcd"]</code>
<strong>输出：</strong><code>4 
<strong>解释</strong></code><strong>：</strong>这两个单词为 <code>"ab", "cd"</code>。</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>words = <code>["a","aa","aaa","aaaa"]</code>
<strong>输出：</strong><code>0 
<strong>解释</strong></code><strong>：</strong><code>不存在这样的两个单词。</code>
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= words.length &lt;= 1000</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 1000</code></li>
	<li><code>words[i]</code>&nbsp;仅包含小写字母</li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
  public int bitNumber(char ch) {
    return (int)ch - (int)'a';
  }

  public int maxProduct(String[] words) {
    int n = words.length;
    int[] masks = new int[n];
    int[] lens = new int[n];

    int bitmask = 0;
    for (int i = 0; i < n; ++i) {
      bitmask = 0;
      for (char ch : words[i].toCharArray()) {
        // add bit number bit_number in bitmask
        bitmask |= 1 << bitNumber(ch);
      }
      masks[i] = bitmask;
      lens[i] = words[i].length();
    }

    int maxVal = 0;
    for (int i = 0; i < n; ++i)
      for (int j = i + 1; j < n; ++j)
        if ((masks[i] & masks[j]) == 0)
          maxVal = Math.max(maxVal, lens[i] * lens[j]);

    return maxVal;
  }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-product-of-word-lengths/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-of-word-lengths/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-product-of-word-lengths/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-product-of-word-lengths/)

[回到目录](../README.md)