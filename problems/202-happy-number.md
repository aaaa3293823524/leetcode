# 202. happy-number | 快乐数

## Question description

<!--If you want to use the English description, use <p>Write an algorithm to determine if a number <code>n</code> is happy.</p>

<p>A <strong>happy number</strong> is a number defined by the following process:</p>

<ul>
	<li>Starting with any positive integer, replace the number by the sum of the squares of its digits.</li>
	<li>Repeat the process until the number equals 1 (where it will stay), or it <strong>loops endlessly in a cycle</strong> which does not include 1.</li>
	<li>Those numbers for which this process <strong>ends in 1</strong> are happy.</li>
</ul>

<p>Return <code>true</code> <em>if</em> <code>n</code> <em>is a happy number, and</em> <code>false</code> <em>if not</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 19
<strong>Output:</strong> true
<strong>Explanation:</strong>
1<sup>2</sup> + 9<sup>2</sup> = 82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 2
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>编写一个算法来判断一个数 <code>n</code> 是不是快乐数。</p>

<p>「快乐数」定义为：</p>

<ul>
	<li>对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和。</li>
	<li>然后重复这个过程直到这个数变为 1，也可能是 <strong>无限循环</strong> 但始终变不到 1。</li>
	<li>如果 <strong>可以变为</strong>&nbsp; 1，那么这个数就是快乐数。</li>
</ul>

<p>如果 <code>n</code> 是快乐数就返回 <code>true</code> ；不是，则返回 <code>false</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 19
<strong>输出：</strong>true
<strong>解释：
</strong>1<sup>2</sup> + 9<sup>2</sup> = 82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 2
<strong>输出：</strong>false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    int bitSquareSum(int n) {
        int sum = 0;
        while(n > 0)
        {
            int bit = n % 10;
            sum += bit * bit;
            n = n / 10;
        }
        return sum;
    }
    
    bool isHappy(int n) {
        int slow = n, fast = bitSquareSum(n);
        while(slow != fast)
        {
            slow = bitSquareSum(slow);
            fast = bitSquareSum(fast);
            fast = bitSquareSum(fast);
        }
        return slow == 1;
    }
};


```

Language: **python3**  /  Runtime: 56 ms

```python3
class Solution:
    def isHappy(self, n: int) -> bool:
        n = str(n)
        visited = set()
        while 1:
            n = str(sum(int(i) ** 2 for i in n))
            if n == "1":
                return True
            if n in visited:
                return False
            visited.add(n)


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/happy-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/happy-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/happy-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/happy-number/)

[回到目录](../README.md)