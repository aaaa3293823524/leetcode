# 128. longest-consecutive-sequence | 最长连续序列

## Question description

<!--If you want to use the English description, use <p>Given an unsorted array of integers <code>nums</code>, return <em>the length of the longest consecutive elements sequence.</em></p>

<p>You must write an algorithm that runs in&nbsp;<code>O(n)</code>&nbsp;time.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [100,4,200,1,3,2]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The longest consecutive elements sequence is <code>[1, 2, 3, 4]</code>. Therefore its length is 4.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,3,7,2,5,8,4,6,0,1]
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定一个未排序的整数数组 <code>nums</code> ，找出数字连续的最长序列（不要求序列元素在原数组中连续）的长度。</p>

<p>请你设计并实现时间复杂度为 <code>O(n)</code><em> </em>的算法解决此问题。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [100,4,200,1,3,2]
<strong>输出：</strong>4
<strong>解释：</strong>最长数字连续序列是 <code>[1, 2, 3, 4]。它的长度为 4。</code></pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [0,3,7,2,5,8,4,6,0,1]
<strong>输出：</strong>9
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= nums.length <= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 341 ms

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        HashMap<Integer,Integer>map=new HashMap<>();
        for(int i=0;i<nums.length;i++){
            map.put(nums[i],1);
        }
        int ans=0;
        for(int i=0;i<nums.length;i++){
            int curLen=1;
            if(!map.containsKey(nums[i]-1)){
                while(map.containsKey(nums[i]+curLen))curLen++;
            }
            ans=Math.max(ans,curLen);
        }

        return ans;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-consecutive-sequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-consecutive-sequence/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-consecutive-sequence/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-consecutive-sequence/)

[回到目录](../README.md)