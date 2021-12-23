# 1974. minimum-time-to-type-word-using-special-typewriter | 使用特殊打字机键入单词的最少时间

## Question description

<!--If you want to use the English description, use <p>There is a special typewriter with lowercase English letters <code>&#39;a&#39;</code> to <code>&#39;z&#39;</code> arranged in a <strong>circle</strong> with a <strong>pointer</strong>. A character can <strong>only</strong> be typed if the pointer is pointing to that character. The pointer is <strong>initially</strong> pointing to the character <code>&#39;a&#39;</code>.</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/31/chart.jpg" style="width: 530px; height: 410px;" />
<p>Each second, you may perform one of the following operations:</p>

<ul>
	<li>Move the pointer one character <strong>counterclockwise</strong> or <strong>clockwise</strong>.</li>
	<li>Type the character the pointer is <strong>currently</strong> on.</li>
</ul>

<p>Given a string <code>word</code>, return the<strong> minimum</strong> number of seconds to type out the characters in <code>word</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;abc&quot;
<strong>Output:</strong> 5
<strong>Explanation: 
</strong>The characters are printed as follows:
- Type the character &#39;a&#39; in 1 second since the pointer is initially on &#39;a&#39;.
- Move the pointer clockwise to &#39;b&#39; in 1 second.
- Type the character &#39;b&#39; in 1 second.
- Move the pointer clockwise to &#39;c&#39; in 1 second.
- Type the character &#39;c&#39; in 1 second.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;bza&quot;
<strong>Output:</strong> 7
<strong>Explanation:
</strong>The characters are printed as follows:
- Move the pointer clockwise to &#39;b&#39; in 1 second.
- Type the character &#39;b&#39; in 1 second.
- Move the pointer counterclockwise to &#39;z&#39; in 2 seconds.
- Type the character &#39;z&#39; in 1 second.
- Move the pointer clockwise to &#39;a&#39; in 1 second.
- Type the character &#39;a&#39; in 1 second.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;zjpc&quot;
<strong>Output:</strong> 34
<strong>Explanation:</strong>
The characters are printed as follows:
- Move the pointer counterclockwise to &#39;z&#39; in 1 second.
- Type the character &#39;z&#39; in 1 second.
- Move the pointer clockwise to &#39;j&#39; in 10 seconds.
- Type the character &#39;j&#39; in 1 second.
- Move the pointer clockwise to &#39;p&#39; in 6 seconds.
- Type the character &#39;p&#39; in 1 second.
- Move the pointer counterclockwise to &#39;c&#39; in 13 seconds.
- Type the character &#39;c&#39; in 1 second.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word.length &lt;= 100</code></li>
	<li><code>word</code> consists of lowercase English letters.</li>
</ul>
 instead-->
<p>有一个特殊打字机，它由一个 <strong>圆盘</strong> 和一个 <strong>指针</strong>&nbsp;组成， 圆盘上标有小写英文字母&nbsp;<code>'a'</code> 到&nbsp;<code>'z'</code>。<strong>只有</strong>&nbsp;当指针指向某个字母时，它才能被键入。指针 <strong>初始时</strong>&nbsp;指向字符 <code>'a'</code>&nbsp;。</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/31/chart.jpg" style="width: 530px; height: 410px;" />
<p>每一秒钟，你可以执行以下操作之一：</p>

<ul>
	<li>将指针 <strong>顺时针</strong>&nbsp;或者 <b>逆时针</b>&nbsp;移动一个字符。</li>
	<li>键入指针 <strong>当前</strong>&nbsp;指向的字符。</li>
</ul>

<p>给你一个字符串&nbsp;<code>word</code>&nbsp;，请你返回键入&nbsp;<code>word</code>&nbsp;所表示单词的 <b>最少</b>&nbsp;秒数&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>word = "abc"
<b>输出：</b>5
<strong>解释：
</strong>单词按如下操作键入：
- 花 1 秒键入字符 'a' in 1 ，因为指针初始指向 'a' ，故不需移动指针。
- 花 1 秒将指针顺时针移到 'b' 。
- 花 1 秒键入字符 'b' 。
- 花 1 秒将指针顺时针移到 'c' 。
- 花 1 秒键入字符 'c' 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>word = "bza"
<b>输出：</b>7
<strong>解释：
</strong>单词按如下操作键入：
- 花 1 秒将指针顺时针移到 'b' 。
- 花 1 秒键入字符 'b' 。
- 花 2 秒将指针逆时针移到 'z' 。
- 花 1 秒键入字符 'z' 。
- 花 1 秒将指针顺时针移到 'a' 。
- 花 1 秒键入字符 'a' 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>word = "zjpc"
<b>输出：</b>34
<strong>解释：</strong>
单词按如下操作键入：
- 花 1 秒将指针逆时针移到 'z' 。
- 花 1 秒键入字符 'z' 。
- 花 10 秒将指针顺时针移到 'j' 。
- 花 1 秒键入字符 'j' 。
- 花 6 秒将指针顺时针移到 'p' 。
- 花 1 秒键入字符 'p' 。
- 花 13 秒将指针逆时针移到 'c' 。
- 花 1 秒键入字符 'c' 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= word.length &lt;= 100</code></li>
	<li><code>word</code>&nbsp;只包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int minTimeToType(String word) {
        int sum=0;
        char[]c=word.toCharArray();
        sum+=Math.min(Math.abs(c[0]-'a'),26-Math.abs(c[0]-'a'))+1;
        for(int i=1;i<c.length;i++) {
            sum=sum+1+Math.min(Math.abs(c[i]-c[i-1]),26-Math.abs(c[i]-c[i-1]));
        }
        return sum;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-time-to-type-word-using-special-typewriter/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-time-to-type-word-using-special-typewriter/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-time-to-type-word-using-special-typewriter/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-time-to-type-word-using-special-typewriter/)

[回到目录](../README.md)