# 377. combination-sum-iv | 组合总和 Ⅳ

## Question description

<!--If you want to use the English description, use <p>Given an array of <strong>distinct</strong> integers <code>nums</code> and a target integer <code>target</code>, return <em>the number of possible combinations that add up to</em>&nbsp;<code>target</code>.</p>

<p>The test cases are generated so that the answer can fit in a <strong>32-bit</strong> integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3], target = 4
<strong>Output:</strong> 7
<strong>Explanation:</strong>
The possible combination ways are:
(1, 1, 1, 1)
(1, 1, 2)
(1, 2, 1)
(1, 3)
(2, 1, 1)
(2, 2)
(3, 1)
Note that different sequences are counted as different combinations.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [9], target = 3
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 200</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 1000</code></li>
	<li>All the elements of <code>nums</code> are <strong>unique</strong>.</li>
	<li><code>1 &lt;= target &lt;= 1000</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> What if negative numbers are allowed in the given array? How does it change the problem? What limitation we need to add to the question to allow negative numbers?</p>
 instead-->
<p>给你一个由 <strong>不同</strong> 整数组成的数组 <code>nums</code> ，和一个目标整数 <code>target</code> 。请你从 <code>nums</code> 中找出并返回总和为 <code>target</code> 的元素组合的个数。</p>

<p>题目数据保证答案符合 32 位整数范围。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3], target = 4
<strong>输出：</strong>7
<strong>解释：</strong>
所有可能的组合为：
(1, 1, 1, 1)
(1, 1, 2)
(1, 2, 1)
(1, 3)
(2, 1, 1)
(2, 2)
(3, 1)
请注意，顺序不同的序列被视作不同的组合。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [9], target = 3
<strong>输出：</strong>0
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 200</code></li>
	<li><code>1 <= nums[i] <= 1000</code></li>
	<li><code>nums</code> 中的所有元素 <strong>互不相同</strong></li>
	<li><code>1 <= target <= 1000</code></li>
</ul>

<p> </p>

<p><strong>进阶：</strong>如果给定的数组中含有负数会发生什么？问题会产生何种变化？如果允许负数出现，需要向题目中添加哪些限制条件？</p>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public int combinationSum4(int[] nums, int target) {
        int ans=0;
        int[]dp=new int[target+1];
        dp[0]=1;
        //Arrays.fill(dp,0);
        //int ans=Integer
        for(int i=1;i<=target;i++) {
            ans=0;
            for(int j=0;j<nums.length;j++) {
                if(i>=nums[j]) {
                ans=ans+dp[i-nums[j]];
                //dp[i]=ans;
                }
                dp[i]=ans;
            }
            System.out.println(dp[i]);
        }
        return dp[target];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/combination-sum-iv/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combination-sum-iv/description/)

Solution: [LeetCode](https://leetcode.com/articles/combination-sum-iv/)  /  [LeetCode中国](https://leetcode-cn.com/articles/combination-sum-iv/)

[回到目录](../README.md)