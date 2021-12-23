# 217. contains-duplicate | 存在重复元素

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, return <code>true</code> if any value appears <strong>at least twice</strong> in the array, and return <code>false</code> if every element is distinct.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3,1]
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3,4]
<strong>Output:</strong> false
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [1,1,1,3,3,4,3,2,4,2]
<strong>Output:</strong> true
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定一个整数数组，判断是否存在重复元素。</p>

<p>如果存在一值在数组中出现至少两次，函数返回 <code>true</code> 。如果数组中每个元素都不相同，则返回 <code>false</code> 。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3,1]
<strong>输出:</strong> true</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入: </strong>[1,2,3,4]
<strong>输出:</strong> false</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入: </strong>[1,1,1,3,3,4,3,2,4,2]
<strong>输出:</strong> true</pre>




## Solution

Language: **java**  /  Runtime: 134 ms

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashMap<Integer, Integer> hashMap=new HashMap<Integer, Integer>();
        for(int i=0;i<nums.length;i++) {
            int t=hashMap.getOrDefault(nums[i],0)+1;
            System.out.println(t);
            if(t>1)return true;
            hashMap.put(nums[i], hashMap.getOrDefault(nums[i],0)+1);
        }
        return false;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/contains-duplicate/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/contains-duplicate/description/)

Solution: [LeetCode](https://leetcode.com/articles/contains-duplicate/)  /  [LeetCode中国](https://leetcode-cn.com/articles/contains-duplicate/)

[回到目录](../README.md)