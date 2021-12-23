# 剑指 Offer 21. diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof | 调整数组顺序使奇数位于偶数前面

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>nums =&nbsp;[1,2,3,4]
<strong>输出：</strong>[1,3,2,4] 
<strong>注：</strong>[3,1,2,4] 也是正确的答案之一。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>0 &lt;= nums.length &lt;= 50000</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10000</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int[] exchange(int[] nums) {
        int[]gg=new int[nums.length];
        int len=nums.length;
        int l=0,h=len-1;
        while(l<h) {
            while(l<len&&(nums[l]&1)==1)l++;
            while(h>=0&&(nums[h]&1)==0)h--;
            if(l<h) {
                nums[l]^=nums[h];
                nums[h]^=nums[l];
                nums[l]^=nums[h];
            }
        }
        
        return nums;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

[回到目录](../README.md)