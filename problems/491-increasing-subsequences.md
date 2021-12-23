# 491. increasing-subsequences | 递增子序列

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, return all the different possible increasing subsequences of the given array with <strong>at least two elements</strong>. You may return the answer in <strong>any order</strong>.</p>

<p>The given array may contain duplicates, and two equal integers should also be considered a special case of increasing sequence.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,6,7,7]
<strong>Output:</strong> [[4,6],[4,6,7],[4,6,7,7],[4,7],[4,7,7],[6,7],[6,7,7],[7,7]]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,4,3,2,1]
<strong>Output:</strong> [[4,4]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 15</code></li>
	<li><code>-100 &lt;= nums[i] &lt;= 100</code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>nums</code> ，找出并返回所有该数组中不同的递增子序列，递增子序列中 <strong>至少有两个元素</strong> 。你可以按 <strong>任意顺序</strong> 返回答案。</p>

<p>数组中可能含有重复元素，如出现两个整数相等，也可以视作递增序列的一种特殊情况。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [4,6,7,7]
<strong>输出：</strong>[[4,6],[4,6,7],[4,6,7,7],[4,7],[4,7,7],[6,7],[6,7,7],[7,7]]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [4,4,3,2,1]
<strong>输出：</strong>[[4,4]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 15</code></li>
	<li><code>-100 &lt;= nums[i] &lt;= 100</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    List<Integer> temp = new ArrayList<Integer>();
    List<List<Integer>> ans = new ArrayList<List<Integer>>();

    public List<List<Integer>> findSubsequences(int[] nums) {
        dfs(0, Integer.MIN_VALUE, nums);
        return ans;
    }

    public void dfs(int cur, int last, int[] nums) {
        if (cur == nums.length) {
            if (temp.size() >= 2) {
                ans.add(new ArrayList<Integer>(temp));
            }
            return;
        }
        if (nums[cur] >= last) {
            temp.add(nums[cur]);
            dfs(cur + 1, nums[cur], nums);
            temp.remove(temp.size() - 1);
        }
        if (nums[cur] != last) {
            dfs(cur + 1, last, nums);
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/increasing-subsequences/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/increasing-subsequences/description/)

Solution: [LeetCode](https://leetcode.com/articles/increasing-subsequences/)  /  [LeetCode中国](https://leetcode-cn.com/articles/increasing-subsequences/)

[回到目录](../README.md)