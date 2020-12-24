# 643. maximum-average-subarray-i | 子数组最大平均数 I

## Question description

<!--If you want to use the English description, use <p>Given an array consisting of <code>n</code> integers, find the contiguous subarray of given length <code>k</code> that has the maximum average value. And you need to output the maximum average value.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> [1,12,-5,-6,50,3], k = 4
<b>Output:</b> 12.75
<b>Explanation:</b> Maximum average is (12-5-6+50)/4 = 51/4 = 12.75
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>1 &lt;= <code>k</code> &lt;= <code>n</code> &lt;= 30,000.</li>
	<li>Elements of the given array will be in the range [-10,000, 10,000].</li>
</ol>

<p>&nbsp;</p>
 instead-->
<p>给定 <code>n</code> 个整数，找出平均数最大且长度为 <code>k</code> 的连续子数组，并输出该最大平均数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,12,-5,-6,50,3], k = 4
<strong>输出:</strong> 12.75
<strong>解释:</strong> 最大平均数 (12-5-6+50)/4 = 51/4 = 12.75
</pre>

<p>&nbsp;</p>

<p><strong>注意:</strong></p>

<ol>
	<li>1 &lt;= <code>k</code> &lt;= <code>n</code> &lt;= 30,000。</li>
	<li>所给数据范围 [-10,000，10,000]。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
class Solution {
    //连续子数组  
    public double findMaxAverage(int[] nums, int k) {
        int sum = 0;
        for(int i=0;i<k;++i){
            sum+=nums[i];
        }
        
        //记录第一个i  和  i+k   sum+nums[i+k-1]-nums[i-1];
        int temp=sum;
        for(int i=1;i+k-1<nums.length;++i){
            temp = temp+nums[i+k-1]-nums[i-1];
            if(temp>sum) sum = temp;
        }
        
        return sum/(double)k;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-average-subarray-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-average-subarray-i/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-average-subarray-i/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-average-subarray-i/)

[回到目录](../README.md)