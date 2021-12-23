# 1799. maximize-score-after-n-operations | N 次操作后的最大分数和

## Question description

<!--If you want to use the English description, use <p>You are given <code>nums</code>, an array of positive integers of size <code>2 * n</code>. You must perform <code>n</code> operations on this array.</p>

<p>In the <code>i<sup>th</sup></code> operation <strong>(1-indexed)</strong>, you will:</p>

<ul>
	<li>Choose two elements, <code>x</code> and <code>y</code>.</li>
	<li>Receive a score of <code>i * gcd(x, y)</code>.</li>
	<li>Remove <code>x</code> and <code>y</code> from <code>nums</code>.</li>
</ul>

<p>Return <em>the maximum score you can receive after performing </em><code>n</code><em> operations.</em></p>

<p>The function <code>gcd(x, y)</code> is the greatest common divisor of <code>x</code> and <code>y</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2]
<strong>Output:</strong> 1
<strong>Explanation:</strong>&nbsp;The optimal choice of operations is:
(1 * gcd(1, 2)) = 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,4,6,8]
<strong>Output:</strong> 11
<strong>Explanation:</strong>&nbsp;The optimal choice of operations is:
(1 * gcd(3, 6)) + (2 * gcd(4, 8)) = 3 + 8 = 11
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5,6]
<strong>Output:</strong> 14
<strong>Explanation:</strong>&nbsp;The optimal choice of operations is:
(1 * gcd(1, 5)) + (2 * gcd(2, 4)) + (3 * gcd(3, 6)) = 1 + 4 + 9 = 14
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 7</code></li>
	<li><code>nums.length == 2 * n</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
</ul>
 instead-->
<p>给你 <code>nums</code> ，它是一个大小为 <code>2 * n</code> 的正整数数组。你必须对这个数组执行 <code>n</code> 次操作。</p>

<p>在第 <code>i</code> 次操作时（操作编号从 <strong>1</strong> 开始），你需要：</p>

<ul>
	<li>选择两个元素 <code>x</code> 和 <code>y</code> 。</li>
	<li>获得分数 <code>i * gcd(x, y)</code> 。</li>
	<li>将 <code>x</code> 和 <code>y</code> 从 <code>nums</code> 中删除。</li>
</ul>

<p>请你返回 <code>n</code> 次操作后你能获得的分数和最大为多少。</p>

<p>函数 <code>gcd(x, y)</code> 是 <code>x</code> 和 <code>y</code> 的最大公约数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>nums = [1,2]
<b>输出：</b>1
<b>解释：</b>最优操作是：
(1 * gcd(1, 2)) = 1
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>nums = [3,4,6,8]
<b>输出：</b>11
<b>解释：</b>最优操作是：
(1 * gcd(3, 6)) + (2 * gcd(4, 8)) = 3 + 8 = 11
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>nums = [1,2,3,4,5,6]
<b>输出：</b>14
<b>解释：</b>最优操作是：
(1 * gcd(1, 5)) + (2 * gcd(2, 4)) + (3 * gcd(3, 6)) = 1 + 4 + 9 = 14
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 7</code></li>
	<li><code>nums.length == 2 * n</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 72 ms

```java
class Solution {
    private int[] arr;
    private int len;
    private int[] memo;
    private int[][] gcdArr;

    private int gcd(int m, int n) {
        return m % n == 0 ? n : gcd(n, m % n);
    }

    private int dp(int num, int idx) {
        if (num == 0) {
            return 0;
        }

        int key = (num << 3) + idx;
        if (memo[key] != 0) {
            return memo[key];
        }

        int ansMax = 0;
        for (int i = 0; i < len; i++) {
            if ((num & (1 << i)) != 0) {
                // 说明这一位可以选
                for (int j = 0; j < len; j++) {
                    if (j == i) {
                        continue;
                    }

                    if ((num & (1 << j)) != 0) {
                        ansMax = Math.max(ansMax, idx * gcdArr[i][j] + dp(num ^ (1 << i) ^ (1 << j), idx + 1));
                    }
                }
            }
        }

        memo[key] = ansMax;
        return ansMax;
    }

    private void calcGcd() {
        gcdArr = new int[len][len];
        for (int i = 0; i < len; i++) {
            for (int j = 0; j < len; j++) {
                gcdArr[i][j] = gcd(arr[i], arr[j]);
            }
        }
    }

    public int maxScore(int[] nums) {
        arr = nums;
        len = arr.length;
        memo = new int[1 << (len + 3)];
        calcGcd();
        return dp((1 << len) - 1, 1);
    }

}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximize-score-after-n-operations/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximize-score-after-n-operations/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximize-score-after-n-operations/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximize-score-after-n-operations/)

[回到目录](../README.md)