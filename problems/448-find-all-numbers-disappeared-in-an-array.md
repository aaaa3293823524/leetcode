# 448. find-all-numbers-disappeared-in-an-array | 找到所有数组中消失的数字

## Question description

<!--If you want to use the English description, use <p>Given an array of integers where 1 &le; a[i] &le; <i>n</i> (<i>n</i> = size of array), some elements appear twice and others appear once.</p>

<p>Find all the elements of [1, <i>n</i>] inclusive that do not appear in this array.</p>

<p>Could you do it without extra space and in O(<i>n</i>) runtime? You may assume the returned list does not count as extra space.</p>

<p><b>Example:</b>
<pre>
<b>Input:</b>
[4,3,2,7,8,2,3,1]

<b>Output:</b>
[5,6]
</pre>
</p> instead-->
<p>给定一个范围在&nbsp; 1 &le; a[i] &le; <em>n</em> (&nbsp;<em>n</em> = 数组大小 ) 的 整型数组，数组中的元素一些出现了两次，另一些只出现一次。</p>

<p>找到所有在 [1, <em>n</em>] 范围之间没有出现在数组中的数字。</p>

<p>您能在不使用额外空间且时间复杂度为<em>O(n)</em>的情况下完成这个任务吗? 你可以假定返回的数组不算在额外空间内。</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong>
[4,3,2,7,8,2,3,1]

<strong>输出:</strong>
[5,6]
</pre>


## Note

**原地修改**


## Solution

Language: **python3**  /  Runtime: 424 ms

```python3
class Solution(object):
    def findDisappearedNumbers(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        
        # Iterate over each of the elements in the original array
        for i in range(len(nums)):
            
            # Treat the value as the new index
            new_index = abs(nums[i]) - 1
            
            # Check the magnitude of value at this new index
            # If the magnitude is positive, make it negative 
            # thus indicating that the number nums[i] has 
            # appeared or has been visited.
            if nums[new_index] > 0:
                nums[new_index] *= -1
        
        # Response array that would contain the missing numbers
        result = []    
        
        # Iterate over the numbers from 1 to N and add all those
        # that have positive magnitude in the array 
        for i in range(1, len(nums) + 1):
            if nums[i - 1] > 0:
                result.append(i)
                
        return result 


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-all-numbers-disappeared-in-an-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-all-numbers-disappeared-in-an-array/)

[回到目录](../README.md)