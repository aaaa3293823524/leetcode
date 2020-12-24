# 260. single-number-iii | 只出现一次的数字 III

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once. You can return the answer in <strong>any order</strong>.</p>

<p><strong>Follow up:&nbsp;</strong>Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?</p>

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
	<li><code>1 &lt;= nums.length &lt;= 30000</code></li>
	<li>&nbsp;Each integer in <code>nums</code> will appear twice, only two integers will appear once.</li>
</ul>
 instead-->
<p>给定一个整数数组&nbsp;<code>nums</code>，其中恰好有两个元素只出现一次，其余所有元素均出现两次。 找出只出现一次的那两个元素。</p>

<p><strong>示例 :</strong></p>

<pre><strong>输入:</strong> <code>[1,2,1,3,2,5]</code>
<strong>输出:</strong> <code>[3,5]</code></pre>

<p><strong>注意：</strong></p>

<ol>
	<li>结果输出的顺序并不重要，对于上面的例子，&nbsp;<code>[5, 3]</code>&nbsp;也是正确答案。</li>
	<li>你的算法应该具有线性时间复杂度。你能否仅使用常数空间复杂度来实现？</li>
</ol>




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