# 1434. number-of-ways-to-wear-different-hats-to-each-other | 每个人戴不同帽子的方案数

## Question description

<!--If you want to use the English description, use <p>There are&nbsp;<code>n</code> people&nbsp;and 40 types of hats labeled from 1 to 40.</p>

<p>Given a list of list of integers <code>hats</code>, where <code>hats[i]</code>&nbsp;is a list of all hats preferred&nbsp;by the <code data-stringify-type="code">i-th</code> person.</p>

<p>Return the number of ways that the n people wear different hats to each other.</p>

<p>Since the answer&nbsp;may be too large,&nbsp;return it modulo&nbsp;<code>10^9 + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> hats = [[3,4],[4,5],[5]]
<strong>Output:</strong> 1
<strong>Explanation: </strong>There is only one way to choose hats given the conditions. 
First person choose hat 3, Second person choose hat 4 and last one hat 5.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> hats = [[3,5,1],[3,5]]
<strong>Output:</strong> 4
<strong>Explanation: </strong>There are 4 ways to choose hats
(3,5), (5,3), (1,3) and (1,5)
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> hats = [[1,2,3,4],[1,2,3,4],[1,2,3,4],[1,2,3,4]]
<strong>Output:</strong> 24
<strong>Explanation: </strong>Each person can choose hats labeled from 1 to 4.
Number of Permutations of (1,2,3,4) = 24.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> hats = [[1,2,3],[2,3,5,6],[1,3,7,9],[1,8,9],[2,5,7]]
<strong>Output:</strong> 111
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == hats.length</code></li>
	<li><code>1 &lt;= n &lt;= 10</code></li>
	<li><code>1 &lt;= hats[i].length &lt;= 40</code></li>
	<li><code>1 &lt;= hats[i][j] &lt;= 40</code></li>
	<li><code>hats[i]</code> contains a list of <strong>unique</strong> integers.</li>
</ul> instead-->
<p>总共有 <code>n</code>&nbsp;个人和 <code>40</code> 种不同的帽子，帽子编号从 <code>1</code> 到 <code>40</code> 。</p>

<p>给你一个整数列表的列表&nbsp;<code>hats</code>&nbsp;，其中&nbsp;<code>hats[i]</code>&nbsp;是第 <code>i</code>&nbsp;个人所有喜欢帽子的列表。</p>

<p>请你给每个人安排一顶他喜欢的帽子，确保每个人戴的帽子跟别人都不一样，并返回方案数。</p>

<p>由于答案可能很大，请返回它对&nbsp;<code>10^9 + 7</code>&nbsp;取余后的结果。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>hats = [[3,4],[4,5],[5]]
<strong>输出：</strong>1
<strong>解释：</strong>给定条件下只有一种方法选择帽子。
第一个人选择帽子 3，第二个人选择帽子 4，最后一个人选择帽子 5。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>hats = [[3,5,1],[3,5]]
<strong>输出：</strong>4
<strong>解释：</strong>总共有 4 种安排帽子的方法：
(3,5)，(5,3)，(1,3) 和 (1,5)
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>hats = [[1,2,3,4],[1,2,3,4],[1,2,3,4],[1,2,3,4]]
<strong>输出：</strong>24
<strong>解释：</strong>每个人都可以从编号为 1 到 4 的帽子中选。
(1,2,3,4) 4 个帽子的排列方案数为 24 。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>hats = [[1,2,3],[2,3,5,6],[1,3,7,9],[1,8,9],[2,5,7]]
<strong>输出：</strong>111
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == hats.length</code></li>
	<li><code>1 &lt;= n &lt;= 10</code></li>
	<li><code>1 &lt;= hats[i].length &lt;= 40</code></li>
	<li><code>1 &lt;= hats[i][j] &lt;= 40</code></li>
	<li><code>hats[i]</code>&nbsp;包含一个数字互不相同的整数列表。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 26 ms

```java
class Solution {
    public int numberWays(List<List<Integer>> hats) {
        final int MOD = 1000000007;
        int n = hats.size();
        // 找到帽子编号的最大值，这样我们只需要求出 f[maxhatid][2^n - 1] 作为答案
        int maxHatId = 0;
        for (int i = 0; i < n; ++i) {
            List<Integer> list = hats.get(i);
            for (int h: list) {
                maxHatId = Math.max(maxHatId, h);
            }
        }
        
        // 对于每一顶帽子 h，hatToPerson[h] 中存储了喜欢这顶帽子的所有人，方便进行动态规划
        List<List<Integer>> hatToPerson = new ArrayList<List<Integer>>();
        for (int i = 0; i <= maxHatId; i++) {
            hatToPerson.add(new ArrayList<Integer>());
        }
        for (int i = 0; i < n; ++i) {
            List<Integer> list = hats.get(i);
            for (int h: list) {
                hatToPerson.get(h).add(i);
            }
        }
        
        int[][] f = new int[maxHatId + 1][1 << n];
        // 边界条件
        f[0][0] = 1;
        for (int i = 1; i <= maxHatId; ++i) {
            for (int mask = 0; mask < (1 << n); ++mask) {
                f[i][mask] = f[i - 1][mask];
                List<Integer> list = hatToPerson.get(i);
                for (int j: list) {
                    if ((mask & (1 << j)) != 0) {
                        f[i][mask] += f[i - 1][mask ^ (1 << j)];
                        f[i][mask] %= MOD;
                    }
                }
            }
        }
        
        return f[maxHatId][(1 << n) - 1];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-ways-to-wear-different-hats-to-each-other/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-ways-to-wear-different-hats-to-each-other/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-ways-to-wear-different-hats-to-each-other/)

[回到目录](../README.md)