# 30. substring-with-concatenation-of-all-words | 串联所有单词的子串

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>s</code> and an array of strings <code>words</code> of <strong>the same length</strong>. Return&nbsp;all starting indices of substring(s) in <code>s</code>&nbsp;that is a concatenation of each word in <code>words</code> <strong>exactly once</strong>, <strong>in any order</strong>,&nbsp;and <strong>without any intervening characters</strong>.</p>

<p>You can return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;barfoothefoobarman&quot;, words = [&quot;foo&quot;,&quot;bar&quot;]
<strong>Output:</strong> [0,9]
<strong>Explanation:</strong> Substrings starting at index 0 and 9 are &quot;barfoo&quot; and &quot;foobar&quot; respectively.
The output order does not matter, returning [9,0] is fine too.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;wordgoodgoodgoodbestword&quot;, words = [&quot;word&quot;,&quot;good&quot;,&quot;best&quot;,&quot;word&quot;]
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;barfoofoobarthefoobarman&quot;, words = [&quot;bar&quot;,&quot;foo&quot;,&quot;the&quot;]
<strong>Output:</strong> [6,9,12]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of lower-case English letters.</li>
	<li><code>1 &lt;= words.length &lt;= 5000</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 30</code></li>
	<li><code>words[i]</code>&nbsp;consists of lower-case English letters.</li>
</ul>
 instead-->
<p>给定一个字符串 <code>s</code><strong> </strong>和一些 <strong>长度相同</strong> 的单词 <code>words</code><strong> 。</strong>找出 <code>s</code><strong> </strong>中恰好可以由 <code>words</code><strong> </strong>中所有单词串联形成的子串的起始位置。</p>

<p>注意子串要与 <code>words</code><strong> </strong>中的单词完全匹配，<strong>中间不能有其他字符 </strong>，但不需要考虑 <code>words</code><strong> </strong>中单词串联的顺序。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "barfoothefoobarman", words = ["foo","bar"]
<strong>输出：</strong><code>[0,9]</code>
<strong>解释：</strong>
从索引 0 和 9 开始的子串分别是 "barfoo" 和 "foobar" 。
输出的顺序不重要, [9,0] 也是有效答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "wordgoodgoodgoodbestword", words = ["word","good","best","word"]
<code><strong>输出：</strong>[]</code>
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "barfoofoobarthefoobarman", words = ["bar","foo","the"]
<strong>输出：</strong>[6,9,12]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 10<sup>4</sup></code></li>
	<li><code>s</code> 由小写英文字母组成</li>
	<li><code>1 <= words.length <= 5000</code></li>
	<li><code>1 <= words[i].length <= 30</code></li>
	<li><code>words[i]</code> 由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 55 ms

```java
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        Map<String, Integer> wordsMap = new HashMap<String, Integer>();
        for (String word : words) {// 单词表
            Integer num = wordsMap.getOrDefault(word, 0) + 1;
            wordsMap.put(word, num);
        }
        int size = words.length;// 单词表个数
        int wordLen = words[0].length();// 每个单词长度
        int total = wordLen * size;// 单词表总长度, s至少要这么长才有可能是
        List<Integer> ans = new ArrayList<>();
        if (s.length() < total) { // 小于就不可能是
            return ans;// 这里不能返回null ... 坑1
        }
        char[] str = s.toCharArray();
        int strLen = s.length();
        for (int i = 0; i < strLen && i + total <= strLen; i++) {// i + total <= strLen 限制最后的起始位置,不足量的不看了
            String part = new String(str, i, wordLen);// 每一个起始点开始,wordLen的字符串
            Integer num = wordsMap.getOrDefault(part, 0);// 在单词表内的数量
            if (num != 0) {// 说明从i开始的长度wordLen字符串,是目标中一个
                // 看看从i开始total长的字符串是不是都是
                boolean has = this.f(str, i, new HashMap<>(wordsMap), wordLen, size, total);
                if (has) {
                    ans.add(i);
                }
            }
        }
        return ans;
    }

    private boolean f(char[] str, int i, HashMap<String, Integer> hashMap, int wordLen, int size, int total) {
        if (str.length - i + 1 < total) {// 长度不够
            return false;
        }
        for (int j = i; j < i + total && j + wordLen <= i + total; j = j + wordLen) {
            String part = new String(str, j, wordLen);
            Integer num = hashMap.getOrDefault(part, 0);
            if (num == 0)
                return false;// 单词表中没有了,这段肯定不是
            else
                hashMap.put(part, num - 1);// 消除一个单词
        }
        return true;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/substring-with-concatenation-of-all-words/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/substring-with-concatenation-of-all-words/description/)

Solution: [LeetCode](https://leetcode.com/articles/substring-with-concatenation-of-all-words/)  /  [LeetCode中国](https://leetcode-cn.com/articles/substring-with-concatenation-of-all-words/)

[回到目录](../README.md)