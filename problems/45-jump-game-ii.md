# 45. jump-game-ii | 跳跃游戏 II

## Question description

<!--If you want to use the English description, use <p>Given an array of non-negative integers <code>nums</code>, you are initially positioned at the first index of the array.</p>

<p>Each element in the array represents your maximum jump length at that position.</p>

<p>Your goal is to reach the last index in the minimum number of jumps.</p>

<p>You can assume that you can always reach the last index.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,3,1,1,4]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,3,0,1,4]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你一个非负整数数组 <code>nums</code> ，你最初位于数组的第一个位置。</p>

<p>数组中的每个元素代表你在该位置可以跳跃的最大长度。</p>

<p>你的目标是使用最少的跳跃次数到达数组的最后一个位置。</p>

<p>假设你总是可以到达数组的最后一个位置。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> nums = [2,3,1,1,4]
<strong>输出:</strong> 2
<strong>解释:</strong> 跳到最后一个位置的最小跳跃数是 <code>2</code>。
     从下标为 0 跳到下标为 1 的位置，跳 <code>1</code> 步，然后跳 <code>3</code> 步到达数组的最后一个位置。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> nums = [2,3,0,1,4]
<strong>输出:</strong> 2
</pre>

<p> </p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 <= nums.length <= 10<sup>4</sup></code></li>
	<li><code>0 <= nums[i] <= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int jump(int[] nums) {
        int length = nums.length;
        int end = 0;
        int maxPosition = 0; 
        int steps = 0;
        for (int i = 0; i < length - 1; i++) {
            maxPosition = Math.max(maxPosition, i + nums[i]); 
            if (i == end) {
                end = maxPosition;
                steps++;
            }
        }
        return steps;
    }
}


```

Language: **python3**  /  Runtime: 204 ms

```python3
class Solution:
    def jump(self, nums: List[int]) -> int:
        
    # 主要思路：在当前最大跳跃步数允许的范围内寻找(当前跳的步数+下次允许跳跃步数)的最大值。

   
        """
        跳跃有游戏
        :param 跳跃步数数组
        """
        # 空的
        if len(nums) == 0:
            return 0

        loc = 0
        count = 0
        # 跳跃
        while loc < len(nums) - 1:
            # 当前可以跳的最大步数
            max_step = nums[loc]
            # 若果直接可以跳到终点
            if (loc + max_step) >= len(nums) - 1:
                loc += max_step
            # 跳不到(贪心法 当前跳得步数+下次可以跳的最大步数 最大)
            else:
                # 查找下一跳的步数
                step = 0
                total_max_step = 0
                for i in range(0, max_step):
                    if (nums[loc + 1 + i] + i + 1) > total_max_step:
                        total_max_step = (nums[loc + 1 + i] + i + 1)
                        step = i + 1
                # 选择最大的
                loc += step
            count += 1

        return count


        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/jump-game-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/jump-game-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/jump-game-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/jump-game-ii/)

[回到目录](../README.md)