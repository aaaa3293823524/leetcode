# 930. binary-subarrays-with-sum | 和相同的二元子数组

## Question description

<!--If you want to use the English description, use <p>In an array <code>A</code> of <code>0</code>s and <code>1</code>s, how many <strong>non-empty</strong> subarrays have sum <code>S</code>?</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-1-1">[1,0,1,0,1]</span>, S = <span id="example-input-1-2">2</span>
<strong>Output: </strong><span id="example-output-1">4</span>
<strong>Explanation: </strong>
The 4 subarrays are bolded below:
[<strong>1,0,1</strong>,0,1]
[<strong>1,0,1,0</strong>,1]
[1,<strong>0,1,0,1</strong>]
[1,0,<strong>1,0,1</strong>]
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>A.length &lt;= 30000</code></li>
	<li><code>0 &lt;= S &lt;= A.length</code></li>
	<li><code>A[i]</code>&nbsp;is either <code>0</code>&nbsp;or <code>1</code>.</li>
</ol> instead-->
<p>在由若干&nbsp;<code>0</code>&nbsp;和&nbsp;<code>1</code>&nbsp; 组成的数组&nbsp;<code>A</code>&nbsp;中，有多少个和为 <code>S</code>&nbsp;的<strong>非空</strong>子数组。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>A = [1,0,1,0,1], S = 2
<strong>输出：</strong>4
<strong>解释：</strong>
如下面黑体所示，有 4 个满足题目要求的子数组：
[<strong>1,0,1</strong>,0,1]
[<strong>1,0,1,0</strong>,1]
[1,<strong>0,1,0,1</strong>]
[1,0,<strong>1,0,1</strong>]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>A.length &lt;= 30000</code></li>
	<li><code>0 &lt;= S &lt;= A.length</code></li>
	<li><code>A[i]</code>&nbsp;为&nbsp;<code>0</code>&nbsp;或&nbsp;<code>1</code></li>
</ol>


## Note

前缀和   P[i] = A[0] + A[1] + ... + A[i - 1]



这样就可以通过 P[j + 1] - P[i] = A[i] + A[i + 1] + ... + A[j] 快速计算出 A[i..j] 的和。



我们可以对数组 P 进行一次线性扫描，当扫描到 P[j] 时，我们需要得到的是满足 P[j] = P[i] + S 且 i < j 的 i 的数目，使用计数器（map 或 dict）可以满足要求





3指针


## Solution

Language: **java**  /  Runtime: 22 ms

```java
class Solution {
    public int numSubarraysWithSum(int[] A, int S) {
        int N = A.length;
        int[] P = new int[N + 1];
        for (int i = 0; i < N; ++i)
            P[i+1] = P[i] + A[i];

        Map<Integer, Integer> count = new HashMap();
        int ans = 0;
        for (int x: P) {
            ans += count.getOrDefault(x, 0);
            count.put(x+S, count.getOrDefault(x+S, 0) + 1);
        }

        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-subarrays-with-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-subarrays-with-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-subarrays-with-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-subarrays-with-sum/)

[回到目录](../README.md)