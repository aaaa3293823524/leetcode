# 剑指 Offer 57. he-wei-sde-liang-ge-shu-zi-lcof | 和为s的两个数字

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [2,7,11,15], target = 9
<strong>输出：</strong>[2,7] 或者 [7,2]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [10,26,30,31,47,60], target = 40
<strong>输出：</strong>[10,30] 或者 [30,10]
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10^5</code></li>
	<li><code>1 &lt;= nums[i]&nbsp;&lt;= 10^6</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 62 ms

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer>map=new HashMap<>();
        for(int i=0;i<nums.length;i++){
            if(map.containsKey(target-nums[i]))return new int[]{nums[i],target-nums[i]};
            else{
                map.put(nums[i],map.getOrDefault(nums[i],0)+1);
            }
        }

        return null;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/he-wei-sde-liang-ge-shu-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/he-wei-sde-liang-ge-shu-zi-lcof/)

[回到目录](../README.md)