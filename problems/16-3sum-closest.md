# 16. 3sum-closest | 最接近的三数之和

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code> of length <code>n</code> and an integer <code>target</code>, find three integers in <code>nums</code> such that the sum is closest to <code>target</code>.</p>

<p>Return <em>the sum of the three integers</em>.</p>

<p>You may assume that each input would have exactly one solution.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,2,1,-4], target = 1
<strong>Output:</strong> 2
<strong>Explanation:</strong> The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,0,0], target = 1
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>-10<sup>4</sup> &lt;= target &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个长度为 <code>n</code> 的整数数组&nbsp;<code>nums</code><em>&nbsp;</em>和 一个目标值&nbsp;<code>target</code>。请你从 <code>nums</code><em> </em>中选出三个整数，使它们的和与&nbsp;<code>target</code>&nbsp;最接近。</p>

<p>返回这三个数的和。</p>

<p>假定每组输入只存在恰好一个解。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [-1,2,1,-4], target = 1
<strong>输出：</strong>2
<strong>解释：</strong>与 target 最接近的和是 2 (-1 + 2 + 1 = 2) 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [0,0,0], target = 1
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>-10<sup>4</sup> &lt;= target &lt;= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);
        int n = nums.length;
        int best = 10000000;

        // 枚举 a
        for (int i = 0; i < n; ++i) {
            // 保证和上一次枚举的元素不相等
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            // 使用双指针枚举 b 和 c
            int j = i + 1, k = n - 1;
            while (j < k) {
                int sum = nums[i] + nums[j] + nums[k];
                // 如果和为 target 直接返回答案
                if (sum == target) {
                    return target;
                }
                // 根据差值的绝对值来更新答案
                if (Math.abs(sum - target) < Math.abs(best - target)) {
                    best = sum;
                }
                if (sum > target) {
                    // 如果和大于 target，移动 c 对应的指针
                    int k0 = k - 1;
                    // 移动到下一个不相等的元素
                    while (j < k0 && nums[k0] == nums[k]) {
                        --k0;
                    }
                    k = k0;
                } else {
                    // 如果和小于 target，移动 b 对应的指针
                    int j0 = j + 1;
                    // 移动到下一个不相等的元素
                    while (j0 < k && nums[j0] == nums[j]) {
                        ++j0;
                    }
                    j = j0;
                }
            }
        }
        return best;
    }
}


```

Language: **python3**  /  Runtime: 172 ms

```python3
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        if len(nums) < 3: return 0
        nums.sort()
        min_diff = sys.maxsize
        for k in range(len(nums) - 2):
            l = k + 1
            r  = len(nums) - 1
            while l < r:
                diff = target - nums[k] - nums[l] - nums[r]
                if abs(diff) < abs(min_diff):
                    min_diff = diff
                if diff == 0:
                    return target
                elif diff > 0:
                    l += 1
                else:
                    r -= 1
        return target - min_diff
```

Language: **cpp**  /  Runtime: 12 ms

```cpp
class Solution {
public:        //利用双指针法进行求解
    int threeSumClosest(vector<int>& nums, int target) {
        if(nums.size() <= 0)
            return 0;
        int distance = INT_MAX , result;
        sort(nums.begin(),nums.end());
        for(int i = 0;i < nums.size();i++)
        {
            if(i > 0 && nums[i] == nums[i-1])
                continue;
            int l = i + 1 , r = nums.size()-1;
            while(l < r)
            {
                int temp = nums[i] + nums[l] + nums[r];
                int dis_temp = abs(temp - target);
                if(temp == target)
                    return target;
                if(dis_temp < distance)
                {
                    result = temp;
                    distance = dis_temp;
                }
                if(temp > target)
                    r--;
                else if(temp < target)
                    l++;
            }    
        }
        return result;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/3sum-closest/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/3sum-closest/description/)

Solution: [LeetCode](https://leetcode.com/articles/3sum-closest/)  /  [LeetCode中国](https://leetcode-cn.com/articles/3sum-closest/)

[回到目录](../README.md)