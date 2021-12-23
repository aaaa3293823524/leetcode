# 剑指 Offer 53 - II. que-shi-de-shu-zi-lcof | 0～n-1中缺失的数字

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [0,1,3]
<strong>输出:</strong> 2
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [0,1,2,3,4,5,6,7,9]
<strong>输出:</strong> 8</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>1 &lt;= 数组长度 &lt;= 10000</code></p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int missingNumber(int[] nums) {
        int i = 0, j = nums.length;
        while(i <j) {
            int m = (i + j) / 2;
            if(nums[m] == m) i = m + 1;
            else j = m ;
        }
        return i;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/que-shi-de-shu-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/que-shi-de-shu-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/que-shi-de-shu-zi-lcof/)

[回到目录](../README.md)