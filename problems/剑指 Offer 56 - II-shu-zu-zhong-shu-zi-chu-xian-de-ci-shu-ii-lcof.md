# 剑指 Offer 56 - II. shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof | 数组中数字出现的次数 II

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>在一个数组 <code>nums</code> 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [3,4,3,3]
<strong>输出：</strong>4
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [9,1,7,9,7,9,7]
<strong>输出：</strong>1</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10000</code></li>
	<li><code>1 &lt;= nums[i] &lt; 2^31</code></li>
</ul>

<p>&nbsp;</p>


## Note

解题思路：

如下图所示，考虑数字的二进制形式，对于出现三次的数字，各 二进制位 出现的次数都是 33 的倍数。

因此，统计所有数字的各二进制位中 11 的出现次数，并对 33 求余，结果则为只出现一次的数字。



有限状态自动机






## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public int singleNumber(int[] nums) {
        int[] counts = new int[32];
        for(int num : nums) {
            for(int j = 0; j < 32; j++) {
                counts[j] += num & 1;
                num >>>= 1;
            }
        }
        int res = 0, m = 3;
        for(int i = 0; i < 32; i++) {
            res <<= 1;
            res |= counts[31 - i] % m;
        }
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

[回到目录](../README.md)