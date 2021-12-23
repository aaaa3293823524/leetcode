# 386. lexicographical-numbers | 字典序排数

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>n</code>, return all the numbers in the range <code>[1, n]</code> sorted in lexicographical order.</p>

<p>You must write an algorithm that runs in&nbsp;<code>O(n)</code>&nbsp;time and uses <code>O(1)</code> extra space.&nbsp;</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 13
<strong>Output:</strong> [1,10,11,12,13,2,3,4,5,6,7,8,9]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> n = 2
<strong>Output:</strong> [1,2]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 5 * 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个整数 <code>n</code> ，按字典序返回范围 <code>[1, n]</code> 内所有整数。</p>

<p>你必须设计一个时间复杂度为 <code>O(n)</code> 且使用 <code>O(1)</code> 额外空间的算法。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 13
<strong>输出：</strong>[1,10,11,12,13,2,3,4,5,6,7,8,9]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 2
<strong>输出：</strong>[1,2]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 5 * 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public List<Integer> lexicalOrder(int n) {
        List<Integer> ans = new ArrayList<>();
        this.f(0, 1, n, ans);
        return ans;
    }

    /**
     * 以base为基数, 从start开始添加到个位数, <=n的结果添加到ans中
     * 
     * @param base
     * @param start
     * @param n
     * @param ans
     */
    private void f(int base, int start, int n, List<Integer> ans) {
        if (base > n)
            return;
        for (int i = start; i < 10; i++) {
            int num = i + base;
            if (num <= n) {
                ans.add(num);
                this.f(num * 10, 0, n, ans);
            }
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/lexicographical-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/lexicographical-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/lexicographical-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/lexicographical-numbers/)

[回到目录](../README.md)