# 剑指 Offer 03. shu-zu-zhong-zhong-fu-de-shu-zi-lcof | 数组中重复的数字

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>找出数组中重复的数字。</p>

<p><br>
在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>
[2, 3, 1, 0, 2, 5, 3]
<strong>输出：</strong>2 或 3 
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>2 &lt;= n &lt;= 100000</code></p>




## Solution

Language: **java**  /  Runtime: 9 ms

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        Map<Integer, Integer>map=new HashMap<>();
        for(int i=0;i<nums.length;i++){
            if(!map.containsKey(nums[i])){
               map.put(nums[i],0);
            }else{
                return nums[i];
            }
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

[回到目录](../README.md)