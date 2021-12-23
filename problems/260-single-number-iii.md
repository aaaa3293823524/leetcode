# 260. single-number-iii | 只出现一次的数字 III

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once. You can return the answer in <strong>any order</strong>.</p>

<p>You must write an&nbsp;algorithm that runs in linear runtime complexity and uses&nbsp;only constant extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,1,3,2,5]
<strong>Output:</strong> [3,5]
<strong>Explanation: </strong> [5, 3] is also a valid answer.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,0]
<strong>Output:</strong> [-1,0]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,1]
<strong>Output:</strong> [1,0]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
	<li>Each integer in <code>nums</code> will appear twice, only two integers will appear once.</li>
</ul>
 instead-->
<p>给定一个整数数组 <code>nums</code>，其中恰好有两个元素只出现一次，其余所有元素均出现两次。 找出只出现一次的那两个元素。你可以按 <strong>任意顺序</strong> 返回答案。</p>

<p> </p>

<p><strong>进阶：</strong>你的算法应该具有线性时间复杂度。你能否仅使用常数空间复杂度来实现？</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,1,3,2,5]
<strong>输出：</strong>[3,5]
<strong>解释：</strong>[5, 3] 也是有效的答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [-1,0]
<strong>输出：</strong>[-1,0]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [0,1]
<strong>输出：</strong>[1,0]
</pre>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 <= nums.length <= 3 * 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> <= nums[i] <= 2<sup>31</sup> - 1</code></li>
	<li>除两个只出现一次的整数外，<code>nums</code> 中的其他数字都出现两次</li>
</ul>




## Solution

Language: **java**  /  Runtime: 17 ms

```java
class Solution {
    public int[] singleNumber(int[] nums) {
        HashMap<Integer, Integer>map=new HashMap<>();
        for(int i=0;i<nums.length;i++) {
            if (!map.containsKey(nums[i])) {
                map.put(nums[i], 1);
            }else {
                map.put(nums[i], map.get(nums[i])+1);
            }
        }
        int a[]=new int[2];
        int index=0;
        for(Map.Entry<Integer, Integer>entry:map.entrySet()) {
            if (entry.getValue()==1) {
                a[index++]=entry.getKey();
            }
        }
        
        return a;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/single-number-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/single-number-iii/description/)

Solution: [LeetCode](https://leetcode.com/articles/single-number-iii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/single-number-iii/)

[回到目录](../README.md)