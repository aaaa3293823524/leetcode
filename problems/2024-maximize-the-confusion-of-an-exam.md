﻿# 2024. maximize-the-confusion-of-an-exam | 考试的最大困扰度

## Question description

<!--If you want to use the English description, use <p>A teacher is writing a test with <code>n</code> true/false questions, with <code>&#39;T&#39;</code> denoting true and <code>&#39;F&#39;</code> denoting false. He wants to confuse the students by <strong>maximizing</strong> the number of <strong>consecutive</strong> questions with the <strong>same</strong> answer (multiple trues or multiple falses in a row).</p>

<p>You are given a string <code>answerKey</code>, where <code>answerKey[i]</code> is the original answer to the <code>i<sup>th</sup></code> question. In addition, you are given an integer <code>k</code>, the maximum number of times you may perform the following operation:</p>

<ul>
	<li>Change the answer key for any question to <code>&#39;T&#39;</code> or <code>&#39;F&#39;</code> (i.e., set <code>answerKey[i]</code> to <code>&#39;T&#39;</code> or <code>&#39;F&#39;</code>).</li>
</ul>

<p>Return <em>the <strong>maximum</strong> number of consecutive</em> <code>&#39;T&#39;</code>s or <code>&#39;F&#39;</code>s <em>in the answer key after performing the operation at most</em> <code>k</code> <em>times</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> answerKey = &quot;TTFF&quot;, k = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> We can replace both the &#39;F&#39;s with &#39;T&#39;s to make answerKey = &quot;<u>TTTT</u>&quot;.
There are four consecutive &#39;T&#39;s.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> answerKey = &quot;TFFT&quot;, k = 1
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can replace the first &#39;T&#39; with an &#39;F&#39; to make answerKey = &quot;<u>FFF</u>T&quot;.
Alternatively, we can replace the second &#39;T&#39; with an &#39;F&#39; to make answerKey = &quot;T<u>FFF</u>&quot;.
In both cases, there are three consecutive &#39;F&#39;s.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> answerKey = &quot;TTFTTFTT&quot;, k = 1
<strong>Output:</strong> 5
<strong>Explanation:</strong> We can replace the first &#39;F&#39; to make answerKey = &quot;<u>TTTTT</u>FTT&quot;
Alternatively, we can replace the second &#39;F&#39; to make answerKey = &quot;TTF<u>TTTTT</u>&quot;. 
In both cases, there are five consecutive &#39;T&#39;s.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == answerKey.length</code></li>
	<li><code>1 &lt;= n &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>answerKey[i]</code> is either <code>&#39;T&#39;</code> or <code>&#39;F&#39;</code></li>
	<li><code>1 &lt;= k &lt;= n</code></li>
</ul>
 instead-->
<p>一位老师正在出一场由 <code>n</code>&nbsp;道判断题构成的考试，每道题的答案为 true （用 <code><span style="">'T'</span></code> 表示）或者 false （用 <code>'F'</code>&nbsp;表示）。老师想增加学生对自己做出答案的不确定性，方法是&nbsp;<strong>最大化&nbsp;</strong>有 <strong>连续相同</strong>&nbsp;结果的题数。（也就是连续出现 true 或者连续出现 false）。</p>

<p>给你一个字符串&nbsp;<code>answerKey</code>&nbsp;，其中&nbsp;<code>answerKey[i]</code>&nbsp;是第 <code>i</code>&nbsp;个问题的正确结果。除此以外，还给你一个整数 <code>k</code>&nbsp;，表示你能进行以下操作的最多次数：</p>

<ul>
	<li>每次操作中，将问题的正确答案改为&nbsp;<code>'T'</code> 或者&nbsp;<code>'F'</code>&nbsp;（也就是将 <code>answerKey[i]</code> 改为&nbsp;<code>'T'</code>&nbsp;或者&nbsp;<code>'F'</code>&nbsp;）。</li>
</ul>

<p>请你返回在不超过 <code>k</code>&nbsp;次操作的情况下，<strong>最大</strong>&nbsp;连续 <code>'T'</code>&nbsp;或者 <code>'F'</code>&nbsp;的数目。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>answerKey = "TTFF", k = 2
<b>输出：</b>4
<b>解释：</b>我们可以将两个 'F' 都变为 'T' ，得到 answerKey = "<em><strong>TTTT</strong></em>" 。
总共有四个连续的 'T' 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>answerKey = "TFFT", k = 1
<b>输出：</b>3
<b>解释：</b>我们可以将最前面的 'T' 换成 'F' ，得到 answerKey = "<em><strong>FFF</strong></em>T" 。
或者，我们可以将第二个 'T' 换成 'F' ，得到 answerKey = "T<em><strong>FFF</strong></em>" 。
两种情况下，都有三个连续的 'F' 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>answerKey = "TTFTTFTT", k = 1
<b>输出：</b>5
<b>解释：</b>我们可以将第一个 'F' 换成 'T' ，得到 answerKey = "<em><strong>TTTTT</strong></em>FTT" 。
或者我们可以将第二个 'F' 换成 'T' ，得到 answerKey = "TTF<em><strong>TTTTT</strong></em>" 。
两种情况下，都有五个连续的 'T' 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == answerKey.length</code></li>
	<li><code>1 &lt;= n &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>answerKey[i]</code>&nbsp;要么是&nbsp;<code>'T'</code> ，要么是&nbsp;<code>'F'</code></li>
	<li><code>1 &lt;= k &lt;= n</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 9 ms

```java
class Solution {
    public int maxConsecutiveAnswers(String answerKey, int k) {
        int n = answerKey.length();
        char[] c = answerKey.toCharArray();
        int left = 0, right = 0;
        int numT = 0, numF = 0;
        int ans = 0;
        while(right < n){
            if(c[right] == 'T')
                numT++;
            else
                numF++;
            while(numT > k && numF > k){
                if(c[left] == 'T')
                    numT--;
                else
                    numF--;
                left++;
            }
            ans = Math.max(ans, right - left + 1);
            right++;
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximize-the-confusion-of-an-exam/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximize-the-confusion-of-an-exam/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximize-the-confusion-of-an-exam/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximize-the-confusion-of-an-exam/)

[回到目录](../README.md)