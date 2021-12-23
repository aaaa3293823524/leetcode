# 1859. sorting-the-sentence | 将句子排序

## Question description

<!--If you want to use the English description, use <p>A <strong>sentence</strong> is a list of words that are separated by a single space with no leading or trailing spaces. Each word consists of lowercase and uppercase English letters.</p>

<p>A sentence can be <strong>shuffled</strong> by appending the <strong>1-indexed word position</strong> to each word then rearranging the words in the sentence.</p>

<ul>
	<li>For example, the sentence <code>&quot;This is a sentence&quot;</code> can be shuffled as <code>&quot;sentence4 a3 is2 This1&quot;</code> or <code>&quot;is2 sentence4 This1 a3&quot;</code>.</li>
</ul>

<p>Given a <strong>shuffled sentence</strong> <code>s</code> containing no more than <code>9</code> words, reconstruct and return <em>the original sentence</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;is2 sentence4 This1 a3&quot;
<strong>Output:</strong> &quot;This is a sentence&quot;
<strong>Explanation:</strong> Sort the words in s to their original positions &quot;This1 is2 a3 sentence4&quot;, then remove the numbers.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Myself2 Me1 I4 and3&quot;
<strong>Output:</strong> &quot;Me Myself and I&quot;
<strong>Explanation:</strong> Sort the words in s to their original positions &quot;Me1 Myself2 and3 I4&quot;, then remove the numbers.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= s.length &lt;= 200</code></li>
	<li><code>s</code> consists of lowercase and uppercase English letters, spaces, and digits from <code>1</code> to <code>9</code>.</li>
	<li>The number of words in <code>s</code> is between <code>1</code> and <code>9</code>.</li>
	<li>The words in <code>s</code> are separated by a single space.</li>
	<li><code>s</code> contains no leading or trailing spaces.</li>
</ul> instead-->
<p>一个 <strong>句子</strong> 指的是一个序列的单词用单个空格连接起来，且开头和结尾没有任何空格。每个单词都只包含小写或大写英文字母。</p>

<p>我们可以给一个句子添加 <strong>从 1 开始的单词位置索引 </strong>，并且将句子中所有单词 <strong>打乱顺序</strong> 。</p>

<ul>
	<li>比方说，句子 <code>"This is a sentence"</code> 可以被打乱顺序得到 <code>"sentence4 a3 is2 This1"</code> 或者 <code>"is2 sentence4 This1 a3"</code> 。</li>
</ul>

<p>给你一个 <strong>打乱顺序</strong> 的句子 <code>s</code> ，它包含的单词不超过 <code>9</code> 个，请你重新构造并得到原本顺序的句子。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>s = "is2 sentence4 This1 a3"
<b>输出：</b>"This is a sentence"
<b>解释：</b>将 s 中的单词按照初始位置排序，得到 "This1 is2 a3 sentence4" ，然后删除数字。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>s = "Myself2 Me1 I4 and3"
<b>输出：</b>"Me Myself and I"
<b>解释：</b>将 s 中的单词按照初始位置排序，得到 "Me1 Myself2 and3 I4" ，然后删除数字。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 <= s.length <= 200</code></li>
	<li><code>s</code> 只包含小写和大写英文字母、空格以及从 <code>1</code> 到 <code>9</code> 的数字。</li>
	<li><code>s</code> 中单词数目为 <code>1</code> 到 <code>9</code> 个。</li>
	<li><code>s</code> 中的单词由单个空格分隔。</li>
	<li><code>s</code> 不包含任何前导或者后缀空格。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public String sortSentence(String s) {
        String strings[]=s.split(" ");
        Arrays.sort(strings,(a,b)->a.charAt(a.length()-1)-b.charAt(b.length()-1));
        StringBuilder stringBuilder=new StringBuilder();
        for(int i=0;i<strings.length;i++) {
            String string=strings[i];
            stringBuilder.append(string.substring(0,string.length()-1)+" ");
        }
        return stringBuilder.toString().substring(0,stringBuilder.length()-1);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sorting-the-sentence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sorting-the-sentence/description/)

Solution: [LeetCode](https://leetcode.com/articles/sorting-the-sentence/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sorting-the-sentence/)

[回到目录](../README.md)