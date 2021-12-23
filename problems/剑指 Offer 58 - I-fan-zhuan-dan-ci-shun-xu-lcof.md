# 剑指 Offer 58 - I. fan-zhuan-dan-ci-shun-xu-lcof | 翻转单词顺序

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p> instead-->
<p>输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串&quot;I am a student. &quot;，则输出&quot;student. a am I&quot;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> &quot;<code>the sky is blue</code>&quot;
<strong>输出:&nbsp;</strong>&quot;<code>blue is sky the</code>&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入:</strong> &quot; &nbsp;hello world! &nbsp;&quot;
<strong>输出:&nbsp;</strong>&quot;world! hello&quot;
<strong>解释: </strong>输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入:</strong> &quot;a good &nbsp; example&quot;
<strong>输出:&nbsp;</strong>&quot;example good a&quot;
<strong>解释: </strong>如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。
</pre>

<p>&nbsp;</p>

<p><strong>说明：</strong></p>

<ul>
	<li>无空格字符构成一个单词。</li>
	<li>输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。</li>
	<li>如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。</li>
</ul>

<p><strong>注意：</strong>本题与主站 151 题相同：<a href="https://leetcode-cn.com/problems/reverse-words-in-a-string/">https://leetcode-cn.com/problems/reverse-words-in-a-string/</a></p>

<p><strong>注意：</strong>此题对比原题有改动</p>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public String reverseWords(String s) {
        String[] strs = s.trim().split(" "); // 删除首尾空格，分割字符串
        StringBuilder res = new StringBuilder();
        for(int i = strs.length - 1; i >= 0; i--) { // 倒序遍历单词列表
            if(strs[i].equals("")) continue; // 遇到空单词则跳过
            res.append(strs[i] + " "); // 将单词拼接至 StringBuilder
        }
        return res.toString().trim(); // 转化为字符串，删除尾部空格，并返回
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/fan-zhuan-dan-ci-shun-xu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fan-zhuan-dan-ci-shun-xu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/fan-zhuan-dan-ci-shun-xu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/fan-zhuan-dan-ci-shun-xu-lcof/)

[回到目录](../README.md)