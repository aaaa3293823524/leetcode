﻿# 977. squares-of-a-sorted-array | 有序数组的平方

## Question description

<!--If you want to use the English description, use <p>Given an array of integers <code>A</code>&nbsp;sorted in non-decreasing order,&nbsp;return an array of the squares of each number,&nbsp;also in sorted non-decreasing order.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[-4,-1,0,3,10]</span>
<strong>Output: </strong><span id="example-output-1">[0,1,9,16,100]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[-7,-3,2,3,11]</span>
<strong>Output: </strong><span id="example-output-2">[4,9,9,49,121]</span>
</pre>

<p>&nbsp;</p>

<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code><span>1 &lt;= A.length &lt;= 10000</span></code></li>
	<li><code>-10000 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>A</code>&nbsp;is sorted in non-decreasing order.</li>
</ol>
</div>
</div> instead-->
<p>给定一个按非递减顺序排序的整数数组 <code>A</code>，返回每个数字的平方组成的新数组，要求也按非递减顺序排序。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[-4,-1,0,3,10]
<strong>输出：</strong>[0,1,9,16,100]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[-7,-3,2,3,11]
<strong>输出：</strong>[4,9,9,49,121]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 10000</code></li>
	<li><code>-10000 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>A</code>&nbsp;已按非递减顺序排序。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public int[] sortedSquares(int[] A) {
        for(int i=0;i<A.length;i++) {
            A[i]=A[i]*A[i];
        }
        Arrays.sort(A);
        return A;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/squares-of-a-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/squares-of-a-sorted-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/squares-of-a-sorted-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/squares-of-a-sorted-array/)

[回到目录](../README.md)