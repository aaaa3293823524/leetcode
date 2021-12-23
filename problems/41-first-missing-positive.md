# 41. first-missing-positive | 缺失的第一个正数

## Question description

<!--If you want to use the English description, use <p>Given an unsorted integer array <code>nums</code>, return the smallest missing positive integer.</p>

<p>You must implement an algorithm that runs in <code>O(n)</code> time and uses constant extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,0]
<strong>Output:</strong> 3
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [3,4,-1,1]
<strong>Output:</strong> 2
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [7,8,9,11,12]
<strong>Output:</strong> 1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给你一个未排序的整数数组 <code>nums</code> ，请你找出其中没有出现的最小的正整数。</p>
请你实现时间复杂度为 <code>O(n)</code> 并且只使用常数级别额外空间的解决方案。

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,0]
<strong>输出：</strong>3
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [3,4,-1,1]
<strong>输出：</strong>2
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [7,8,9,11,12]
<strong>输出：</strong>1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 5 * 10<sup>5</sup></code></li>
	<li><code>-2<sup>31</sup> <= nums[i] <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        for (int i = 0; i < nums.length; i++){
            //如果nums[i]在1到nums.length之间，就进行归位
            //仔细理解nums[nums[i] - 1] != nums[i]
            //比如现在nums[i]==5，那么我们就要看下标为4 (即nums[i] - 1)的位置，看下标为4的位置上放的是不是5 (即nums[i])，如果下标为4的地方存放的是其他的数字，就进行交换，把5归位
            while (nums[i] > 0 && nums[i] <= nums.length && nums[nums[i] - 1] != nums[i]){
                swap(nums, i, nums[i] - 1);
            }
        }
        //从头遍历归位后的数组，如果当前存储的数字并不是 下标 + 1，那么缺失的就是这个数字
        for (int i = 0; i < nums.length; i++){
            if (nums[i] != i + 1) return i + 1;
        }
        //1到nums.length都出现了，返回nums.length + 1
        return nums.length + 1;
    }

    public void swap(int[] nums, int i, int j){
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/first-missing-positive/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/first-missing-positive/description/)

Solution: [LeetCode](https://leetcode.com/articles/first-missing-positive/)  /  [LeetCode中国](https://leetcode-cn.com/articles/first-missing-positive/)

[回到目录](../README.md)