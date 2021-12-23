# 164. maximum-gap | 最大间距

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, return <em>the maximum difference between two successive elements in its sorted form</em>. If the array contains less than two elements, return <code>0</code>.</p>

<p>You must write an algorithm that runs in linear time and uses linear extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,6,9,1]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The sorted form of the array is [1,3,6,9], either (3,6) or (6,9) has the maximum difference 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [10]
<strong>Output:</strong> 0
<strong>Explanation:</strong> The array contains less than 2 elements, therefore return 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定一个无序的数组，找出数组在排序之后，相邻元素之间最大的差值。</p>

<p>如果数组元素个数小于 2，则返回 0。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [3,6,9,1]
<strong>输出:</strong> 3
<strong>解释:</strong> 排序后的数组是 [1,3,6,9]<strong><em>, </em></strong>其中相邻元素 (3,6) 和 (6,9) 之间都存在最大差值 3。</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [10]
<strong>输出:</strong> 0
<strong>解释:</strong> 数组元素个数小于 2，因此返回 0。</pre>

<p><strong>说明:</strong></p>

<ul>
	<li>你可以假设数组中所有元素都是非负整数，且数值在 32 位有符号整数范围内。</li>
	<li>请尝试在线性时间复杂度和空间复杂度的条件下解决此问题。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 89 ms

```java
class Solution {
    public int maximumGap(int[] nums) {
        int n = nums.length;
        if (n < 2) {
            return 0;
        }
        int minVal = Arrays.stream(nums).min().getAsInt();
        int maxVal = Arrays.stream(nums).max().getAsInt();
        int d = Math.max(1, (maxVal - minVal) / (n - 1));
        int bucketSize = (maxVal - minVal) / d + 1;

        int[][] bucket = new int[bucketSize][2];
        for (int i = 0; i < bucketSize; ++i) {
            Arrays.fill(bucket[i], -1); // 存储 (桶内最小值，桶内最大值) 对， (-1, -1) 表示该桶是空的
        }
        for (int i = 0; i < n; i++) {
            int idx = (nums[i] - minVal) / d;
            if (bucket[idx][0] == -1) {
                bucket[idx][0] = bucket[idx][1] = nums[i];
            } else {
                bucket[idx][0] = Math.min(bucket[idx][0], nums[i]);
                bucket[idx][1] = Math.max(bucket[idx][1], nums[i]);
            }
        }

        int ret = 0;
        int prev = -1;
        for (int i = 0; i < bucketSize; i++) {
            if (bucket[i][0] == -1) {
                continue;
            }
            if (prev != -1) {
                ret = Math.max(ret, bucket[i][0] - bucket[prev][1]);
            }
            prev = i;
        }
        return ret;
    }
}


```

Language: **python3**  /  Runtime: 148 ms

```python3
class Solution:
    def maximumGap(self, nums: List[int]) -> int:
        l=len(nums)
        if(l<2):return 0
        
        nums.sort()
        num=1
        max=abs(nums[1]-nums[0])
        for i in nums[2:]:
            if(abs(i-nums[num])>max):
                max=(i-nums[num])
            num+=1
        return max
            
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-gap/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-gap/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-gap/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-gap/)

[回到目录](../README.md)