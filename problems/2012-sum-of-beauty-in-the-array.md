# 2012. sum-of-beauty-in-the-array | 数组美丽值求和

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>0-indexed</strong> integer array <code>nums</code>. For each index <code>i</code> (<code>1 &lt;= i &lt;= nums.length - 2</code>) the <strong>beauty</strong> of <code>nums[i]</code> equals:</p>

<ul>
	<li><code>2</code>, if <code>nums[j] &lt; nums[i] &lt; nums[k]</code>, for <strong>all</strong> <code>0 &lt;= j &lt; i</code> and for <strong>all</strong> <code>i &lt; k &lt;= nums.length - 1</code>.</li>
	<li><code>1</code>, if <code>nums[i - 1] &lt; nums[i] &lt; nums[i + 1]</code>, and the previous condition is not satisfied.</li>
	<li><code>0</code>, if none of the previous conditions holds.</li>
</ul>

<p>Return<em> the <strong>sum of beauty</strong> of all </em><code>nums[i]</code><em> where </em><code>1 &lt;= i &lt;= nums.length - 2</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> 2
<strong>Explanation:</strong> For each index i in the range 1 &lt;= i &lt;= 1:
- The beauty of nums[1] equals 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,4,6,4]
<strong>Output:</strong> 1
<strong>Explanation:</strong> For each index i in the range 1 &lt;= i &lt;= 2:
- The beauty of nums[1] equals 1.
- The beauty of nums[2] equals 0.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,2,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> For each index i in the range 1 &lt;= i &lt;= 1:
- The beauty of nums[1] equals 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>给你一个下标从 <strong>0</strong> 开始的整数数组 <code>nums</code> 。对于每个下标 <code>i</code>（<code>1 &lt;= i &lt;= nums.length - 2</code>），<code>nums[i]</code> 的 <strong>美丽值</strong> 等于：</p>

<ul>
	<li><code>2</code>，对于所有 <code>0 &lt;= j &lt; i</code> 且 <code>i &lt; k &lt;= nums.length - 1</code> ，满足 <code>nums[j] &lt; nums[i] &lt; nums[k]</code></li>
	<li><code>1</code>，如果满足 <code>nums[i - 1] &lt; nums[i] &lt; nums[i + 1]</code> ，且不满足前面的条件</li>
	<li><code>0</code>，如果上述条件全部不满足</li>
</ul>

<p>返回符合 <code>1 &lt;= i &lt;= nums.length - 2</code> 的所有<em> </em><code>nums[i]</code><em> </em>的 <strong>美丽值的总和</strong> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [1,2,3]
<strong>输出：</strong>2
<strong>解释：</strong>对于每个符合范围 1 &lt;= i &lt;= 1 的下标 i :
- nums[1] 的美丽值等于 2
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [2,4,6,4]
<strong>输出：</strong>1
<strong>解释：</strong>对于每个符合范围 1 &lt;= i &lt;= 2 的下标 i :
- nums[1] 的美丽值等于 1
- nums[2] 的美丽值等于 0
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>nums = [3,2,1]
<strong>输出：</strong>0
<strong>解释：</strong>对于每个符合范围 1 &lt;= i &lt;= 1 的下标 i :
- nums[1] 的美丽值等于 0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int sumOfBeauties(int[] nums) {
        int n = nums.length;
        
        //保存左边最大
        int max = nums[0];
        //保存右边最小
        int min = nums[n - 1];
        
        //初始化状态数组，保存当前数是否满足条件
        boolean[] tmp = new boolean[n];
        for(int i = 0 ; i < n ; i++){
            tmp[i] = false;
        }
        
        //先从左开始遍历
        for(int i = 1 ; i <= n - 2 ; ++i){
            //中间数如果大于左边最大，说明这个数左半边都满足条件
            if(max < nums[i]){
                tmp[i] = true;
                max = nums[i];
            }
        }
        
        //再从右开始遍历
        for(int i = n - 2 ; i >= 1 ; --i){
            //中间数如果小于右边最小，说明这个数右半边都满足条件
            if(nums[i] < min){
                min = nums[i];
            }else{ //不满足需要重置为false，防止只满足左边的情况
                tmp[i] = false;
            }
        }
        
        int res = 0;
        for(int i = 1 ; i <= n - 2 ; ++i){
            if(tmp[i]){
                res += 2;
            }else if(nums[i-1] < nums[i] && nums[i] < nums[i+1]){
                res += 1;
            }
        }
        
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-beauty-in-the-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-beauty-in-the-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-beauty-in-the-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-beauty-in-the-array/)

[回到目录](../README.md)