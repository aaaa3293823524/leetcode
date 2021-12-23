# 915. partition-array-into-disjoint-intervals | 分割数组

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, partition it into two (contiguous) subarrays <code>left</code> and <code>right</code> so that:</p>

<ul>
	<li>Every element in <code>left</code> is less than or equal to every element in <code>right</code>.</li>
	<li><code>left</code> and <code>right</code> are non-empty.</li>
	<li><code>left</code> has the smallest possible size.</li>
</ul>

<p>Return <em>the length of </em><code>left</code><em> after such a partitioning</em>.</p>

<p>Test cases are generated such that partitioning exists.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,0,3,8,6]
<strong>Output:</strong> 3
<strong>Explanation:</strong> left = [5,0,3], right = [8,6]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,1,0,6,12]
<strong>Output:</strong> 4
<strong>Explanation:</strong> left = [1,1,1,0], right = [6,12]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li>There is at least one valid answer for the given input.</li>
</ul>
 instead-->
<p>给定一个数组 <code>A</code>，将其划分为两个连续子数组 <code>left</code> 和 <code>right</code>， 使得：</p>

<ul>
	<li><code>left</code> 中的每个元素都小于或等于 <code>right</code> 中的每个元素。</li>
	<li><code>left</code> 和 <code>right</code> 都是非空的。</li>
	<li><code>left</code> 的长度要尽可能小。</li>
</ul>

<p>在完成这样的分组后返回 <code>left</code> 的<strong>长度</strong>。可以保证存在这样的划分方法。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>[5,0,3,8,6]
<strong>输出：</strong>3
<strong>解释：</strong>left = [5,0,3]，right = [8,6]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>[1,1,1,0,6,12]
<strong>输出：</strong>4
<strong>解释：</strong>left = [1,1,1,0]，right = [6,12]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>2 <= A.length <= 30000</code></li>
	<li><code>0 <= A[i] <= 10^6</code></li>
	<li>可以保证至少有一种方法能够按题目所描述的那样对 <code>A</code> 进行划分。</li>
</ol>

<p> </p>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int partitionDisjoint(int[] nums) {
        int n=nums.length;
        int[]dp=new int[n];//下标之前最大值
        dp[0]=nums[0];
        int end=0;
        for(int i=1;i<nums.length;i++){
            if(nums[i]>dp[i-1]) {
                dp[i] = nums[i];
                
            }else{
                dp[i]=dp[i-1];
                //end=i;
            }
        }
        for(int i=1;i<nums.length;i++){
            boolean flag=false;
            for(int j=i;j<nums.length;j++){
                if(nums[j]<dp[i-1]){
                    flag=true;
                    break;
                }
            }
            if(!flag)return i;
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/partition-array-into-disjoint-intervals/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/partition-array-into-disjoint-intervals/description/)

Solution: [LeetCode](https://leetcode.com/articles/partition-array-into-disjoint-intervals/)  /  [LeetCode中国](https://leetcode-cn.com/articles/partition-array-into-disjoint-intervals/)

[回到目录](../README.md)