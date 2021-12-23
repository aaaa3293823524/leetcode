# 738. monotone-increasing-digits | 单调递增的数字

## Question description

<!--If you want to use the English description, use <p>An integer has <strong>monotone increasing digits</strong> if and only if each pair of adjacent digits <code>x</code> and <code>y</code> satisfy <code>x &lt;= y</code>.</p>

<p>Given an integer <code>n</code>, return <em>the largest number that is less than or equal to </em><code>n</code><em> with <strong>monotone increasing digits</strong></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> 9
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 1234
<strong>Output:</strong> 1234
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 332
<strong>Output:</strong> 299
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定一个非负整数&nbsp;<code>N</code>，找出小于或等于&nbsp;<code>N</code>&nbsp;的最大的整数，同时这个整数需要满足其各个位数上的数字是单调递增。</p>

<p>（当且仅当每个相邻位数上的数字&nbsp;<code>x</code>&nbsp;和&nbsp;<code>y</code>&nbsp;满足&nbsp;<code>x &lt;= y</code>&nbsp;时，我们称这个整数是单调递增的。）</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> N = 10
<strong>输出:</strong> 9
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> N = 1234
<strong>输出:</strong> 1234
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> N = 332
<strong>输出:</strong> 299
</pre>

<p><strong>说明:</strong> <code>N</code>&nbsp;是在&nbsp;<code>[0, 10^9]</code>&nbsp;范围内的一个整数。</p>




## Solution

Language: **python3**  /  Runtime: 56 ms

```python3
class Solution:
    def monotoneIncreasingDigits(self, N: int) -> int:
        nums = list(str(N))
        length = len(nums)
        begin = 0
        # N 是否符合条件
        is_result = True
        max_num = float('-inf')
        
        # 从前往后观察
        for i in range(1, length):
            num = int(nums[i])
            pre_num = int(nums[i - 1])
            # 记录最大值
            if pre_num > max_num:
                begin = i - 1
                max_num = pre_num
            if pre_num > num:
                is_result = False
                break
        
        # 如果 N 本身符合条件，直接返回 N
        if is_result:
            return N
        
        # begin 位置减去 1，后面全部替换为 9
        nums[begin] = str(int(nums[begin]) - 1)
        for i in range(begin + 1, length):
            nums[i] = '9'
                    
        return int("".join(nums))


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/monotone-increasing-digits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/monotone-increasing-digits/description/)

Solution: [LeetCode](https://leetcode.com/articles/monotone-increasing-digits/)  /  [LeetCode中国](https://leetcode-cn.com/articles/monotone-increasing-digits/)

[回到目录](../README.md)