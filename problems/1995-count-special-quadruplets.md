# 1995. count-special-quadruplets | 统计特殊四元组

## Question description

<!--If you want to use the English description, use <p>Given a <strong>0-indexed</strong> integer array <code>nums</code>, return <em>the number of <strong>distinct</strong> quadruplets</em> <code>(a, b, c, d)</code> <em>such that:</em></p>

<ul>
	<li><code>nums[a] + nums[b] + nums[c] == nums[d]</code>, and</li>
	<li><code>a &lt; b &lt; c &lt; d</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,6]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The only quadruplet that satisfies the requirement is (0, 1, 2, 3) because 1 + 2 + 3 == 6.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,3,6,4,5]
<strong>Output:</strong> 0
<strong>Explanation:</strong> There are no such quadruplets in [3,3,6,4,5].
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,1,3,5]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The 4 quadruplets that satisfy the requirement are:
- (0, 1, 2, 3): 1 + 1 + 1 == 3
- (0, 1, 3, 4): 1 + 1 + 3 == 5
- (0, 2, 3, 4): 1 + 1 + 3 == 5
- (1, 2, 3, 4): 1 + 1 + 3 == 5
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>4 &lt;= nums.length &lt;= 50</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 100</code></li>
</ul>
 instead-->
<p>给你一个 <strong>下标从 0 开始</strong> 的整数数组 <code>nums</code> ，返回满足下述条件的 <strong>不同</strong> 四元组 <code>(a, b, c, d)</code> 的 <strong>数目</strong> ：</p>

<ul>
	<li><code>nums[a] + nums[b] + nums[c] == nums[d]</code> ，且</li>
	<li><code>a &lt; b &lt; c &lt; d</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [1,2,3,6]
<strong>输出：</strong>1
<strong>解释：</strong>满足要求的唯一一个四元组是 (0, 1, 2, 3) 因为 1 + 2 + 3 == 6 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [3,3,6,4,5]
<strong>输出：</strong>0
<strong>解释：</strong>[3,3,6,4,5] 中不存在满足要求的四元组。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>nums = [1,1,1,3,5]
<strong>输出：</strong>4
<strong>解释：</strong>满足要求的 4 个四元组如下：
- (0, 1, 2, 3): 1 + 1 + 1 == 3
- (0, 1, 3, 4): 1 + 1 + 3 == 5
- (0, 2, 3, 4): 1 + 1 + 3 == 5
- (1, 2, 3, 4): 1 + 1 + 3 == 5
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>4 &lt;= nums.length &lt;= 50</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 100</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 38 ms

```java
class Solution {
    public int countQuadruplets(int[] nums) {
        int n = nums.length;
        if (n < 4) return 0;
        if (n == 4) return (nums[0]+nums[1]+nums[2]) == nums[3] ? 1 : 0;
        Map<Integer, Integer> map1 = new HashMap<>();
        Map<Integer, Integer> map2 = new HashMap<>();
        Map<Integer, Integer> map3 = new HashMap<>();
        int cnt = 0;
        for (int num:nums) {
            if (map3.containsKey(num)) {
                cnt += map3.getOrDefault(num, 0);
            }
            for (Map.Entry<Integer, Integer> entry: map2.entrySet()) {
                int tmp = entry.getKey() + num;
                map3.put(tmp, map3.getOrDefault(tmp, 0) + entry.getValue());
            }
            for (Map.Entry<Integer, Integer> entry: map1.entrySet()) {
                int tmp = entry.getKey() + num;
                map2.put(tmp, map2.getOrDefault(tmp, 0) + entry.getValue());
            }
            map1.put(num, map1.getOrDefault(num, 0) + 1);
        }
        return cnt;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/count-special-quadruplets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-special-quadruplets/description/)

Solution: [LeetCode](https://leetcode.com/articles/count-special-quadruplets/)  /  [LeetCode中国](https://leetcode-cn.com/articles/count-special-quadruplets/)

[回到目录](../README.md)