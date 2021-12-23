﻿# 2042. check-if-numbers-are-ascending-in-a-sentence | 检查句子中的数字是否递增

## Question description

<!--If you want to use the English description, use <p>A sentence is a list of <strong>tokens</strong> separated by a <strong>single</strong> space with no leading or trailing spaces. Every token is either a <strong>positive number</strong> consisting of digits <code>0-9</code> with no leading zeros, or a <strong>word</strong> consisting of lowercase English letters.</p>

<ul>
	<li>For example, <code>&quot;a puppy has 2 eyes 4 legs&quot;</code> is a sentence with seven tokens: <code>&quot;2&quot;</code> and <code>&quot;4&quot;</code> are numbers and the other tokens such as <code>&quot;puppy&quot;</code> are words.</li>
</ul>

<p>Given a string <code>s</code> representing a sentence, you need to check if <strong>all</strong> the numbers in <code>s</code> are <strong>strictly increasing</strong> from left to right (i.e., other than the last number, <strong>each</strong> number is <strong>strictly smaller</strong> than the number on its <strong>right</strong> in <code>s</code>).</p>

<p>Return <code>true</code><em> if so, or </em><code>false</code><em> otherwise</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="example-1" src="https://assets.leetcode.com/uploads/2021/09/30/example1.png" style="width: 637px; height: 48px;" />
<pre>
<strong>Input:</strong> s = &quot;1 box has 3 blue 4 red 6 green and 12 yellow marbles&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> The numbers in s are: 1, 3, 4, 6, 12.
They are strictly increasing from left to right: 1 &lt; 3 &lt; 4 &lt; 6 &lt; 12.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;hello world 5 x 5&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> The numbers in s are: <u><strong>5</strong></u>, <strong><u>5</u></strong>. They are not strictly increasing.
</pre>

<p><strong>Example 3:</strong></p>
<img alt="example-3" src="https://assets.leetcode.com/uploads/2021/09/30/example3.png" style="width: 794px; height: 48px;" />
<pre>
<strong>Input:</strong> s = &quot;sunset is at 7 51 pm overnight lows will be in the low 50 and 60 s&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> The numbers in s are: 7, <u><strong>51</strong></u>, <u><strong>50</strong></u>, 60. They are not strictly increasing.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;4 5 11 26&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> The numbers in s are: 4, 5, 11, 26.
They are strictly increasing from left to right: 4 &lt; 5 &lt; 11 &lt; 26.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 200</code></li>
	<li><code>s</code> consists of lowercase English letters, spaces, and digits from <code>0</code> to <code>9</code>, inclusive.</li>
	<li>The number of tokens in <code>s</code> is between <code>2</code> and <code>100</code>, inclusive.</li>
	<li>The tokens in <code>s</code> are separated by a single space.</li>
	<li>There are at least <strong>two</strong> numbers in <code>s</code>.</li>
	<li>Each number in <code>s</code> is a <strong>positive</strong> number <strong>less</strong> than <code>100</code>, with no leading zeros.</li>
	<li><code>s</code> contains no leading or trailing spaces.</li>
</ul>
 instead-->
<p>句子是由若干 <strong>token</strong> 组成的一个列表，<strong>token</strong> 间用 <strong>单个</strong> 空格分隔，句子没有前导或尾随空格。每个 token 要么是一个由数字 <code>0-9</code> 组成的不含前导零的 <strong>正整数</strong>&nbsp;，要么是一个由小写英文字母组成的 <strong>单词</strong> 。</p>

<ul>
	<li>示例，<code>"a puppy has 2 eyes 4 legs"</code> 是一个由 7 个 token 组成的句子：<code>"2"</code> 和 <code>"4"</code> 是数字，其他像&nbsp;<code>"puppy"</code> 这样的 tokens 属于单词。</li>
</ul>

<p>给你一个表示句子的字符串 <code>s</code> ，你需要检查 <code>s</code> 中的 <strong>全部</strong> 数字是否从左到右严格递增（即，除了最后一个数字，<code>s</code> 中的 <strong>每个</strong> 数字都严格小于它 <strong>右侧</strong> 的数字）。</p>

<p>如果满足题目要求，返回 <code>true</code>&nbsp;，否则，返回<em> </em><code>false</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="example-1" src="https://assets.leetcode.com/uploads/2021/09/30/example1.png" style="width: 637px; height: 48px;" /></p>

<pre>
<strong>输入：</strong>s = "1 box has 3 blue 4 red 6 green and 12 yellow marbles"
<strong>输出：</strong>true
<strong>解释：</strong>句子中的数字是：1, 3, 4, 6, 12 。
这些数字是按从左到右严格递增的 1 &lt; 3 &lt; 4 &lt; 6 &lt; 12 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "hello world 5 x 5"
<strong>输出：</strong>false
<strong>解释：</strong>句子中的数字是：<em><strong>5</strong></em>, <strong><em>5</em></strong> 。这些数字不是严格递增的。
</pre>

<p><strong>示例 3：</strong></p>

<p><img alt="example-3" src="https://assets.leetcode.com/uploads/2021/09/30/example3.png" style="width: 794px; height: 48px;" /></p>

<pre>
<strong>输入：</strong>s = "sunset is at 7 51 pm overnight lows will be in the low 50 and 60 s"
<strong>输出：</strong>false
<strong>解释：</strong>s 中的数字是：7, <em><strong>51</strong></em>, <em><strong>50</strong></em>, 60 。这些数字不是严格递增的。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>s = "4 5 11 26"
<strong>输出：</strong>true
<strong>解释：</strong>s 中的数字是：4, 5, 11, 26 。
这些数字是按从左到右严格递增的：4 &lt; 5 &lt; 11 &lt; 26 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 200</code></li>
	<li><code>s</code> 由小写英文字母、空格和数字 <code>0</code> 到 <code>9</code> 组成（包含 <code>0</code> 和 <code>9</code>）</li>
	<li><code>s</code> 中数字 token 的数目在 <code>2</code> 和 <code>100</code> 之间（包含 <code>2</code> 和 <code>100</code>）</li>
	<li><code>s</code> 中的 token 之间由单个空格分隔</li>
	<li><code>s</code> 中至少有 <strong>两个</strong> 数字</li>
	<li><code>s</code> 中的每个数字都是一个 <strong>小于</strong> <code>100</code> 的 <strong>正</strong> 数，且不含前导零</li>
	<li><code>s</code> 不含前导或尾随空格</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public boolean areNumbersAscending(String s) {
        String[] strings=s.split(" ");
        int pre=-1;
        for(int i=0;i<strings.length;i++) {
            if(!Character.isAlphabetic(strings[i].charAt(0))) {
                int t=Integer.valueOf(strings[i]);
                if(t<=pre)return false;
                else {
                    pre=t;
                }
            }
        }
        return true;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/check-if-numbers-are-ascending-in-a-sentence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/check-if-numbers-are-ascending-in-a-sentence/description/)

Solution: [LeetCode](https://leetcode.com/articles/check-if-numbers-are-ascending-in-a-sentence/)  /  [LeetCode中国](https://leetcode-cn.com/articles/check-if-numbers-are-ascending-in-a-sentence/)

[回到目录](../README.md)