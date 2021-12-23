# 823. binary-trees-with-factors | 带因子的二叉树

## Question description

<!--If you want to use the English description, use <p>Given an array of unique integers, <code>arr</code>, where each integer <code>arr[i]</code> is strictly greater than <code>1</code>.</p>

<p>We make a binary tree using these integers, and each number may be used for any number of times. Each non-leaf node&#39;s value should be equal to the product of the values of its children.</p>

<p>Return <em>the number of binary trees we can make</em>. The answer may be too large so return the answer <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [2,4]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can make these trees: <code>[2], [4], [4, 2, 2]</code></pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [2,4,5,10]
<strong>Output:</strong> 7
<strong>Explanation:</strong> We can make these trees: <code>[2], [4], [5], [10], [4, 2, 2], [10, 2, 5], [10, 5, 2]</code>.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 1000</code></li>
	<li><code>2 &lt;= arr[i] &lt;= 10<sup>9</sup></code></li>
	<li>All the values of <code>arr</code> are <strong>unique</strong>.</li>
</ul>
 instead-->
<p>给出一个含有不重复整数元素的数组 <code>arr</code> ，每个整数 <code>arr[i]</code> 均大于 1。</p>

<p>用这些整数来构建二叉树，每个整数可以使用任意次数。其中：每个非叶结点的值应等于它的两个子结点的值的乘积。</p>

<p>满足条件的二叉树一共有多少个？答案可能很大，返回<strong> 对 </strong><code>10<sup>9</sup> + 7</code> <strong>取余</strong> 的结果。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> <code>arr = [2, 4]</code>
<strong>输出:</strong> 3
<strong>解释:</strong> 可以得到这些二叉树: <code>[2], [4], [4, 2, 2]</code></pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> <code>arr = [2, 4, 5, 10]</code>
<strong>输出:</strong> <code>7</code>
<strong>解释:</strong> 可以得到这些二叉树: <code>[2], [4], [5], [10], [4, 2, 2], [10, 2, 5], [10, 5, 2]</code>.</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 1000</code></li>
	<li><code>2 &lt;= arr[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>arr</code> 中的所有值 <strong>互不相同</strong></li>
</ul>




## Solution

Language: **java**  /  Runtime: 18 ms

```java
class Solution {
    public int numFactoredBinaryTrees(int[] A) {
        int MOD = 1_000_000_007;
        int N = A.length;
        Arrays.sort(A);
        long[] dp = new long[N];
        Arrays.fill(dp, 1);

        Map<Integer, Integer> index = new HashMap();
        for (int i = 0; i < N; ++i)
            index.put(A[i], i);

        for (int i = 0; i < N; ++i)
            for (int j = 0; j < i; ++j) {
                if (A[i] % A[j] == 0) { // A[j] is left child
                    int right = A[i] / A[j];
                    if (index.containsKey(right)) {
                        dp[i] = (dp[i] + dp[j] * dp[index.get(right)]) % MOD;
                    }
                }
            }

        long ans = 0;
        for (long x: dp) ans += x;
        return (int) (ans % MOD);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-trees-with-factors/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-trees-with-factors/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-trees-with-factors/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-trees-with-factors/)

[回到目录](../README.md)