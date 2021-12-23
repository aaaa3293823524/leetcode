# 996. number-of-squareful-arrays | 正方形数组的数目

## Question description

<!--If you want to use the English description, use <p>An array is <strong>squareful</strong> if the sum of every pair of adjacent elements is a <strong>perfect square</strong>.</p>

<p>Given an integer array nums, return <em>the number of permutations of </em><code>nums</code><em> that are <strong>squareful</strong></em>.</p>

<p>Two permutations <code>perm1</code> and <code>perm2</code> are different if there is some index <code>i</code> such that <code>perm1[i] != perm2[i]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,17,8]
<strong>Output:</strong> 2
<strong>Explanation:</strong> [1,8,17] and [17,8,1] are the valid permutations.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,2,2]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 12</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定一个非负整数数组&nbsp;<code>A</code>，如果该数组每对相邻元素之和是一个完全平方数，则称这一数组为<em>正方形</em>数组。</p>

<p>返回 A 的正方形排列的数目。两个排列 <code>A1</code> 和 <code>A2</code> 不同的充要条件是存在某个索引 <code>i</code>，使得 A1[i] != A2[i]。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[1,17,8]
<strong>输出：</strong>2
<strong>解释：</strong>
[1,8,17] 和 [17,8,1] 都是有效的排列。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[2,2,2]
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 12</code></li>
	<li><code>0 &lt;= A[i] &lt;= 1e9</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 11 ms

```java
class Solution {
    int N;
    Map<Integer, List<Integer>> graph;
    Integer[][] memo;

    public int numSquarefulPerms(int[] A) {
        N = A.length;
        graph = new HashMap();
        memo = new Integer[N][1 << N];

        for (int i = 0; i < N; ++i)
            graph.put(i, new ArrayList());

        for (int i = 0; i < N; ++i)
            for (int j = i+1; j < N; ++j) {
                int r = (int) (Math.sqrt(A[i] + A[j]) + 0.5);
                if (r * r == A[i] + A[j]) {
                    graph.get(i).add(j);
                    graph.get(j).add(i);
                }
            }


        int[] factorial = new int[20];
        factorial[0] = 1;
        for (int i = 1; i < 20; ++i)
            factorial[i] = i * factorial[i-1];

        int ans = 0;
        for (int i = 0; i < N; ++i)
            ans += dfs(i, 1 << i);

        Map<Integer, Integer> count = new HashMap();
        for (int x: A)
            count.put(x, count.getOrDefault(x, 0) + 1);
        for (int v: count.values())
            ans /= factorial[v];

        return ans;
    }

    public int dfs(int node, int visited) {
        if (visited == (1 << N) - 1)
            return 1;
        if (memo[node][visited] != null)
            return memo[node][visited];

        int ans = 0;
        for (int nei: graph.get(node))
            if (((visited >> nei) & 1) == 0)
                ans += dfs(nei, visited | (1 << nei));
        memo[node][visited] = ans;
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-squareful-arrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-squareful-arrays/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-squareful-arrays/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-squareful-arrays/)

[回到目录](../README.md)