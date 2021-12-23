# 剑指 Offer 56 - I. shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof | 数组中数字出现的次数

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>一个整型数组 <code>nums</code> 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [4,1,4,6]
<strong>输出：</strong>[1,6] 或 [6,1]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [1,2,10,4,1,4,3,3]
<strong>输出：</strong>[2,10] 或 [10,2]</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10000</code></li>
</ul>

<p>&nbsp;</p>


## Note

分组异或


## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int ret = 0;
        for (int n : nums) {
            ret ^= n;
        }
        int div = 1;
        while ((div & ret) == 0) {
            div <<= 1;
        }
        int a = 0, b = 0;
        for (int n : nums) {
            if ((div & n) != 0) {
                a ^= n;
            } else {
                b ^= n;
            }
        }
        return new int[]{a, b};
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

[回到目录](../README.md)