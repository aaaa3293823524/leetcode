# 801. minimum-swaps-to-make-sequences-increasing | 使序列递增的最小交换次数

## Question description

<!--If you want to use the English description, use <p>You are given two integer arrays of the same length <code>nums1</code> and <code>nums2</code>. In one operation, you are allowed to swap <code>nums1[i]</code> with <code>nums2[i]</code>.</p>

<ul>
	<li>For example, if <code>nums1 = [1,2,3,<u>8</u>]</code>, and <code>nums2 = [5,6,7,<u>4</u>]</code>, you can swap the element at <code>i = 3</code> to obtain <code>nums1 = [1,2,3,4]</code> and <code>nums2 = [5,6,7,8]</code>.</li>
</ul>

<p>Return <em>the minimum number of needed operations to make </em><code>nums1</code><em> and </em><code>nums2</code><em> <strong>strictly increasing</strong></em>. The test cases are generated so that the given input always makes it possible.</p>

<p>An array <code>arr</code> is <strong>strictly increasing</strong> if and only if <code>arr[0] &lt; arr[1] &lt; arr[2] &lt; ... &lt; arr[arr.length - 1]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,3,5,4], nums2 = [1,2,3,7]
<strong>Output:</strong> 1
<strong>Explanation:</strong> 
Swap nums1[3] and nums2[3]. Then the sequences are:
nums1 = [1, 3, 5, 7] and nums2 = [1, 2, 3, 4]
which are both strictly increasing.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [0,3,5,8,9], nums2 = [2,1,4,6,9]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums1.length &lt;= 10<sup>5</sup></code></li>
	<li><code>nums2.length == nums1.length</code></li>
	<li><code>0 &lt;= nums1[i], nums2[i] &lt;= 2 * 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>我们有两个长度相等且不为空的整型数组&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;。</p>

<p>我们可以交换&nbsp;<code>A[i]</code>&nbsp;和&nbsp;<code>B[i]</code>&nbsp;的元素。注意这两个元素在各自的序列中应该处于相同的位置。</p>

<p>在交换过一些元素之后，数组&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;都应该是严格递增的（数组严格递增的条件仅为<code>A[0] &lt; A[1] &lt; A[2] &lt; ... &lt; A[A.length - 1]</code>）。</p>

<p>给定数组&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;，请返回使得两个数组均保持严格递增状态的最小交换次数。假设给定的输入总是有效的。</p>

<pre>
<strong>示例:</strong>
<strong>输入:</strong> A = [1,3,5,4], B = [1,2,3,7]
<strong>输出:</strong> 1
<strong>解释: </strong>
交换 A[3] 和 B[3] 后，两个数组如下:
A = [1, 3, 5, 7] ， B = [1, 2, 3, 4]
两个数组均为严格递增的。</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>A, B</code>&nbsp;两个数组的长度总是相等的，且长度的范围为&nbsp;<code>[1, 1000]</code>。</li>
	<li><code>A[i], B[i]</code>&nbsp;均为&nbsp;<code>[0, 2000]</code>区间内的整数。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int minSwap(int[] A, int[] B) {
        // n: natural, s: swapped
        int n1 = 0, s1 = 1;
        for (int i = 1; i < A.length; ++i) {
            int n2 = Integer.MAX_VALUE, s2 = Integer.MAX_VALUE;
            if (A[i-1] < A[i] && B[i-1] < B[i]) {
                n2 = Math.min(n2, n1);
                s2 = Math.min(s2, s1 + 1);
            }
            if (A[i-1] < B[i] && B[i-1] < A[i]) {
                n2 = Math.min(n2, s1);
                s2 = Math.min(s2, n1 + 1);
            }
            n1 = n2;
            s1 = s2;
        }
        return Math.min(n1, s1);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-swaps-to-make-sequences-increasing/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-swaps-to-make-sequences-increasing/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-swaps-to-make-sequences-increasing/)

[回到目录](../README.md)