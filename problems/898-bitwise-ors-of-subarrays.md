# 898. bitwise-ors-of-subarrays | 子数组按位或操作

## Question description

<!--If you want to use the English description, use <p>We have an array <code>arr</code> of non-negative integers.</p>

<p>For every (contiguous) subarray <code>sub = [arr[i], arr[i + 1], ..., arr[j]]</code> (with <code>i &lt;= j</code>), we take the bitwise OR of all the elements in <code>sub</code>, obtaining a result <code>arr[i] | arr[i + 1] | ... | arr[j]</code>.</p>

<p>Return the number of possible results. Results that occur more than once are only counted once in the final answer</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [0]
<strong>Output:</strong> 1
<strong>Explanation:</strong> There is only one possible result: 0.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,1,2]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The possible subarrays are [1], [1], [2], [1, 1], [1, 2], [1, 1, 2].
These yield the results 1, 1, 2, 1, 3, 3.
There are 3 unique values, so the answer is 3.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,2,4]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The possible results are 1, 2, 3, 4, 6, and 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= nums[i]&nbsp;&lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>我们有一个非负整数数组&nbsp;<code>A</code>。</p>

<p>对于每个（连续的）子数组&nbsp;<code>B =&nbsp;[A[i], A[i+1], ..., A[j]]</code> （&nbsp;<code>i &lt;= j</code>），我们对&nbsp;<code>B</code>&nbsp;中的每个元素进行按位或操作，获得结果&nbsp;<code>A[i] | A[i+1] | ... | A[j]</code>。</p>

<p>返回可能结果的数量。 （多次出现的结果在最终答案中仅计算一次。）</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[0]
<strong>输出：</strong>1
<strong>解释：</strong>
只有一个可能的结果 0 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[1,1,2]
<strong>输出：</strong>3
<strong>解释：</strong>
可能的子数组为 [1]，[1]，[2]，[1, 1]，[1, 2]，[1, 1, 2]。
产生的结果为 1，1，2，1，3，3 。
有三个唯一值，所以答案是 3 。
</pre>

<p><strong>示例&nbsp;3：</strong></p>

<pre><strong>输入：</strong>[1,2,4]
<strong>输出：</strong>6
<strong>解释：</strong>
可能的结果是 1，2，3，4，6，以及 7 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 50000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 10^9</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 408 ms

```java
class Solution {
    public int subarrayBitwiseORs(int[] A) {
        Set<Integer> ans = new HashSet();
        Set<Integer> cur = new HashSet();
        cur.add(0);
        for (int x: A) {
            Set<Integer> cur2 = new HashSet();
            for (int y: cur)
                cur2.add(x | y);
            cur2.add(x);
            cur = cur2;
            ans.addAll(cur);
        }

        return ans.size();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/bitwise-ors-of-subarrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/bitwise-ors-of-subarrays/description/)

Solution: [LeetCode](https://leetcode.com/articles/bitwise-ors-of-subarrays/)  /  [LeetCode中国](https://leetcode-cn.com/articles/bitwise-ors-of-subarrays/)

[回到目录](../README.md)