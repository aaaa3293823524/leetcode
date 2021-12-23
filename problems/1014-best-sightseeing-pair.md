# 1014. best-sightseeing-pair | 最佳观光组合

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>values</code> where values[i] represents the value of the <code>i<sup>th</sup></code> sightseeing spot. Two sightseeing spots <code>i</code> and <code>j</code> have a <strong>distance</strong> <code>j - i</code> between them.</p>

<p>The score of a pair (<code>i &lt; j</code>) of sightseeing spots is <code>values[i] + values[j] + i - j</code>: the sum of the values of the sightseeing spots, minus the distance between them.</p>

<p>Return <em>the maximum score of a pair of sightseeing spots</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> values = [8,1,5,2,6]
<strong>Output:</strong> 11
<strong>Explanation:</strong> i = 0, j = 2, values[i] + values[j] + i - j = 8 + 5 + 0 - 2 = 11
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> values = [1,2]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= values.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= values[i] &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你一个正整数数组 <code>values</code>，其中 <code>values[i]</code> 表示第 <code>i</code> 个观光景点的评分，并且两个景点 <code>i</code> 和 <code>j</code> 之间的 <strong>距离</strong> 为 <code>j - i</code>。</p>

<p>一对景点（<code>i < j</code>）组成的观光组合的得分为 <code>values[i] + values[j] + i - j</code> ，也就是景点的评分之和<strong> 减去 </strong>它们两者之间的距离。</p>

<p>返回一对观光景点能取得的最高分。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>values = [8,1,5,2,6]
<strong>输出：</strong>11
<strong>解释：</strong>i = 0, j = 2, values[i] + values[j] + i - j = 8 + 5 + 0 - 2 = 11
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>values = [1,2]
<strong>输出：</strong>2
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 <= values.length <= 5 * 10<sup>4</sup></code></li>
	<li><code>1 <= values[i] <= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public int maxScoreSightseeingPair(int[] values) {
        int ans = 0, mx = values[0] + 0;
        for (int j = 1; j < values.length; ++j) {
            ans = Math.max(ans, mx + values[j] - j);
            // 边遍历边维护
            mx = Math.max(mx, values[j] + j);
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/best-sightseeing-pair/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-sightseeing-pair/description/)

Solution: [LeetCode](https://leetcode.com/articles/best-sightseeing-pair/)  /  [LeetCode中国](https://leetcode-cn.com/articles/best-sightseeing-pair/)

[回到目录](../README.md)