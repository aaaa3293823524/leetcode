# 1991. find-the-middle-index-in-array | 找到数组的中间位置

## Question description

<!--If you want to use the English description, use <p>Given a <strong>0-indexed</strong> integer array <code>nums</code>, find the <strong>leftmost</strong> <code>middleIndex</code> (i.e., the smallest amongst all the possible ones).</p>

<p>A <code>middleIndex</code> is an index where <code>nums[0] + nums[1] + ... + nums[middleIndex-1] == nums[middleIndex+1] + nums[middleIndex+2] + ... + nums[nums.length-1]</code>.</p>

<p>If <code>middleIndex == 0</code>, the left side sum is considered to be <code>0</code>. Similarly, if <code>middleIndex == nums.length - 1</code>, the right side sum is considered to be <code>0</code>.</p>

<p>Return <em>the <strong>leftmost</strong> </em><code>middleIndex</code><em> that satisfies the condition, or </em><code>-1</code><em> if there is no such index</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,3,-1,<u>8</u>,4]
<strong>Output:</strong> 3
<strong>Explanation:</strong>
The sum of the numbers before index 3 is: 2 + 3 + -1 = 4
The sum of the numbers after index 3 is: 4 = 4
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,-1,<u>4</u>]
<strong>Output:</strong> 2
<strong>Explanation:</strong>
The sum of the numbers before index 2 is: 1 + -1 = 0
The sum of the numbers after index 2 is: 0
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,5]
<strong>Output:</strong> -1
<strong>Explanation:</strong>
There is no valid middleIndex.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> nums = [<u>1</u>]
<strong>Output:</strong> 0
<strong>Explantion:</strong>
The sum of the numbers before index 0 is: 0
The sum of the numbers after index 0 is: 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Note:</strong> This question is the same as&nbsp;724:&nbsp;<a href="https://leetcode.com/problems/find-pivot-index/" target="_blank">https://leetcode.com/problems/find-pivot-index/</a></p>
 instead-->
<p>给你一个下标从 <strong>0</strong>&nbsp;开始的整数数组&nbsp;<code>nums</code>&nbsp;，请你找到 <strong>最左边</strong>&nbsp;的中间位置&nbsp;<code>middleIndex</code>&nbsp;（也就是所有可能中间位置下标最小的一个）。</p>

<p>中间位置&nbsp;<code>middleIndex</code>&nbsp;是满足&nbsp;<code>nums[0] + nums[1] + ... + nums[middleIndex-1] == nums[middleIndex+1] + nums[middleIndex+2] + ... + nums[nums.length-1]</code>&nbsp;的数组下标。</p>

<p>如果&nbsp;<code>middleIndex == 0</code>&nbsp;，左边部分的和定义为 <code>0</code>&nbsp;。类似的，如果&nbsp;<code>middleIndex == nums.length - 1</code>&nbsp;，右边部分的和定义为&nbsp;<code>0</code>&nbsp;。</p>

<p>请你返回满足上述条件 <strong>最左边</strong>&nbsp;的<em>&nbsp;</em><code>middleIndex</code>&nbsp;，如果不存在这样的中间位置，请你返回&nbsp;<code>-1</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>nums = [2,3,-1,<em><strong>8</strong></em>,4]
<b>输出：</b>3
<strong>解释：</strong>
下标 3 之前的数字和为：2 + 3 + -1 = 4
下标 3 之后的数字和为：4 = 4
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>nums = [1,-1,<em><strong>4</strong></em>]
<b>输出：</b>2
<strong>解释：</strong>
下标 2 之前的数字和为：1 + -1 = 0
下标 2 之后的数字和为：0
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>nums = [2,5]
<b>输出：</b>-1
<b>解释：</b>
不存在符合要求的 middleIndex 。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<b>输入：</b>nums = [<em><strong>1</strong></em>]
<b>输出：</b>0
<strong>解释：</strong>
下标 0 之前的数字和为：0
下标 0 之后的数字和为：0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>注意：</strong>本题与主站 724 题相同：<a href="https://leetcode-cn.com/problems/find-pivot-index/" target="_blank">https://leetcode-cn.com/problems/find-pivot-index/</a></p>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int findMiddleIndex(int[] nums) {
        int[]sum=new int[nums.length];
        sum[0]=nums[0];
        for(int i=1;i<nums.length;i++) {
            sum[i]=sum[i-1]+nums[i];
        }
        for(int i=0;i<nums.length;i++) {
            //System.out.println(sum[nums.length-1]-sum[i]);
            //System.out.println(sum[i]-nums[0]
            if((sum[nums.length-1]-sum[i])==(sum[i]-nums[i]))return i;
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-the-middle-index-in-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-the-middle-index-in-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-the-middle-index-in-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-the-middle-index-in-array/)

[回到目录](../README.md)