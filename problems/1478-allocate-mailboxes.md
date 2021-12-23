# 1478. allocate-mailboxes | 安排邮筒

## Question description

<!--If you want to use the English description, use <p>Given the array <code>houses</code> and an integer <code>k</code>. where <code>houses[i]</code> is the location of the ith house along a street, your task is to allocate <code>k</code> mailboxes in&nbsp;the street.</p>

<p>Return the <strong>minimum</strong> total distance between each house and its nearest mailbox.</p>

<p>The answer is guaranteed to fit in a 32-bit signed integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/05/07/sample_11_1816.png" style="width: 454px; height: 154px;" /></p>

<pre>
<strong>Input:</strong> houses = [1,4,8,10,20], k = 3
<strong>Output:</strong> 5
<strong>Explanation: </strong>Allocate mailboxes in position 3, 9 and 20.
Minimum total distance from each houses to nearest mailboxes is |3-1| + |4-3| + |9-8| + |10-9| + |20-20| = 5 
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2020/05/07/sample_2_1816.png" style="width: 433px; height: 154px;" /></strong></p>

<pre>
<strong>Input:</strong> houses = [2,3,5,12,18], k = 2
<strong>Output:</strong> 9
<strong>Explanation: </strong>Allocate mailboxes in position 3 and 14.
Minimum total distance from each houses to nearest mailboxes is |2-3| + |3-3| + |5-3| + |12-14| + |18-14| = 9.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> houses = [7,4,6,1], k = 1
<strong>Output:</strong> 8
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> houses = [3,6,14,10], k = 4
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == houses.length</code></li>
	<li><code>1 &lt;= n&nbsp;&lt;= 100</code></li>
	<li><code>1 &lt;= houses[i] &lt;= 10^4</code></li>
	<li><code>1 &lt;= k &lt;= n</code></li>
	<li>Array <code>houses</code> contain unique integers.</li>
</ul> instead-->
<p>给你一个房屋数组<code>houses</code>&nbsp;和一个整数&nbsp;<code>k</code>&nbsp;，其中&nbsp;<code>houses[i]</code>&nbsp;是第 <code>i</code>&nbsp;栋房子在一条街上的位置，现需要在这条街上安排 <code>k</code>&nbsp;个邮筒。</p>

<p>请你返回每栋房子与离它最近的邮筒之间的距离的 <strong>最小 </strong>总和。</p>

<p>答案保证在 32 位有符号整数范围以内。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/06/13/sample_11_1816.png" style="height: 154px; width: 454px;"></p>

<pre><strong>输入：</strong>houses = [1,4,8,10,20], k = 3
<strong>输出：</strong>5
<strong>解释：</strong>将邮筒分别安放在位置 3， 9 和 20 处。
每个房子到最近邮筒的距离和为 |3-1| + |4-3| + |9-8| + |10-9| + |20-20| = 5 。
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/06/13/sample_2_1816.png" style="height: 154px; width: 433px;"></strong></p>

<pre><strong>输入：</strong>houses = [2,3,5,12,18], k = 2
<strong>输出：</strong>9
<strong>解释：</strong>将邮筒分别安放在位置 3 和 14 处。
每个房子到最近邮筒距离和为 |2-3| + |3-3| + |5-3| + |12-14| + |18-14| = 9 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>houses = [7,4,6,1], k = 1
<strong>输出：</strong>8
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>houses = [3,6,14,10], k = 4
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == houses.length</code></li>
	<li><code>1 &lt;= n&nbsp;&lt;= 100</code></li>
	<li><code>1 &lt;= houses[i] &lt;= 10^4</code></li>
	<li><code>1 &lt;= k &lt;= n</code></li>
	<li>数组&nbsp;<code>houses</code>&nbsp;中的整数互不相同。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
class Solution {
    public int minDistance(int[] houses, int k) {
        int n = houses.length;
        Arrays.sort(houses);

        int[][] medsum = new int[n][n];
        for (int i = n - 2; i >= 0; --i) {
            for (int j = i + 1; j < n; ++j) {
                medsum[i][j] = medsum[i + 1][j - 1] + houses[j] - houses[i];
            }
        }

        int[][] f = new int[n][k + 1];
        for (int i = 0; i < n; ++i) {
            Arrays.fill(f[i], Integer.MAX_VALUE / 2);
        }
        for (int i = 0; i < n; ++i) {
            f[i][1] = medsum[0][i];
            for (int j = 2; j <= k && j <= i + 1; ++j) {
                for (int i0 = 0; i0 < i; ++i0) {
                    f[i][j] = Math.min(f[i][j], f[i0][j - 1] + medsum[i0 + 1][i]);
                }
            }
        }

        return f[n - 1][k];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/allocate-mailboxes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/allocate-mailboxes/description/)

Solution: [LeetCode](https://leetcode.com/articles/allocate-mailboxes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/allocate-mailboxes/)

[回到目录](../README.md)