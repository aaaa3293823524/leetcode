# 39. combination-sum | 组合总和

## Question description

<!--If you want to use the English description, use <p>Given an array of <strong>distinct</strong> integers <code>candidates</code> and a target integer <code>target</code>, return <em>a list of all <strong>unique combinations</strong> of </em><code>candidates</code><em> where the chosen numbers sum to </em><code>target</code><em>.</em> You may return the combinations in <strong>any order</strong>.</p>

<p>The <strong>same</strong> number may be chosen from <code>candidates</code> an <strong>unlimited number of times</strong>. Two combinations are unique if the frequency of at least one of the chosen numbers is different.</p>

<p>It is <strong>guaranteed</strong> that the number of unique combinations that sum up to <code>target</code> is less than <code>150</code> combinations for the given input.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> candidates = [2,3,6,7], target = 7
<strong>Output:</strong> [[2,2,3],[7]]
<strong>Explanation:</strong>
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> candidates = [2,3,5], target = 8
<strong>Output:</strong> [[2,2,2,2],[2,3,3],[3,5]]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> candidates = [2], target = 1
<strong>Output:</strong> []
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> candidates = [1], target = 1
<strong>Output:</strong> [[1]]
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> candidates = [1], target = 2
<strong>Output:</strong> [[1,1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= candidates.length &lt;= 30</code></li>
	<li><code>1 &lt;= candidates[i] &lt;= 200</code></li>
	<li>All elements of <code>candidates</code> are <strong>distinct</strong>.</li>
	<li><code>1 &lt;= target &lt;= 500</code></li>
</ul>
 instead-->
<p>给定一个<strong>无重复元素</strong>的数组&nbsp;<code>candidates</code>&nbsp;和一个目标数&nbsp;<code>target</code>&nbsp;，找出&nbsp;<code>candidates</code>&nbsp;中所有可以使数字和为&nbsp;<code>target</code>&nbsp;的组合。</p>

<p><code>candidates</code>&nbsp;中的数字可以无限制重复被选取。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>所有数字（包括&nbsp;<code>target</code>）都是正整数。</li>
	<li>解集不能包含重复的组合。&nbsp;</li>
</ul>

<p><strong>示例&nbsp;1：</strong></p>

<pre><strong>输入：</strong>candidates = <code>[2,3,6,7], </code>target = <code>7</code>,
<strong>所求解集为：</strong>
[
  [7],
  [2,2,3]
]
</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入：</strong>candidates = [2,3,5]<code>, </code>target = 8,
<strong>所求解集为：</strong>
[
&nbsp; [2,2,2,2],
&nbsp; [2,3,3],
&nbsp; [3,5]
]</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= candidates.length &lt;= 30</code></li>
	<li><code>1 &lt;= candidates[i] &lt;= 200</code></li>
	<li><code>candidate</code> 中的每个元素都是独一无二的。</li>
	<li><code>1 &lt;= target &lt;= 500</code></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 116 ms

```python3
class Solution:
    def combinationSum(self, candidates, target):
        ans = []
        temp = []
        def recursion(idx, res):
            if idx >= len(candidates) or res >= target:
                if res == target:
                    ans.append(temp[:])
                return
            temp.append(candidates[idx])
            recursion(idx, res + candidates[idx]) 
            temp.pop()
            recursion(idx + 1, res)
        recursion(0, 0)
        return ans 
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/combination-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combination-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/combination-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/combination-sum/)

[回到目录](../README.md)