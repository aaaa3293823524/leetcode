# 283. move-zeroes | 移动零

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, move all <code>0</code>&#39;s to the end of it while maintaining the relative order of the non-zero elements.</p>

<p><strong>Note</strong> that you must do this in-place without making a copy of the array.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [0,1,0,3,12]
<strong>Output:</strong> [1,3,12,0,0]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> [0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you minimize the total number of operations done? instead-->
<p>给定一个数组 <code>nums</code>，编写一个函数将所有 <code>0</code> 移动到数组的末尾，同时保持非零元素的相对顺序。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>[0,1,0,3,12]</code>
<strong>输出:</strong> <code>[1,3,12,0,0]</code></pre>

<p><strong>说明</strong>:</p>

<ol>
	<li>必须在原数组上操作，不能拷贝额外的数组。</li>
	<li>尽量减少操作次数。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public static void moveZeroes(int[] nums) {
        int len=nums.length;
        int b[]=new int[len];
        Arrays.fill(b, 0);
        int index=0;
        for(int i=0;i<len;i++) {
            if (nums[i]!=0) {
                b[index++]=nums[i];
            }
        }
        for(int i=0;i<len;i++) {
            nums[i]=b[i];
        }
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/move-zeroes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/move-zeroes/description/)

Solution: [LeetCode](https://leetcode.com/articles/move-zeroes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/move-zeroes/)

[回到目录](../README.md)