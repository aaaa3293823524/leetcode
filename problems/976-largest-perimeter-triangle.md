# 976. largest-perimeter-triangle | 三角形的最大周长

## Question description

<!--If you want to use the English description, use <p>Given an array <code>A</code> of positive lengths, return the largest perimeter of a triangle with <strong>non-zero area</strong>, formed from 3 of these lengths.</p>

<p>If it is impossible to form any&nbsp;triangle of non-zero area, return <code>0</code>.</p>

<p>&nbsp;</p>

<ol>
</ol>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[2,1,2]</span>
<strong>Output: </strong><span id="example-output-1">5</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[1,2,1]</span>
<strong>Output: </strong><span id="example-output-2">0</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">[3,2,3,4]</span>
<strong>Output: </strong><span id="example-output-3">10</span>
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-4-1">[3,6,2,3]</span>
<strong>Output: </strong><span id="example-output-4">8</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>3 &lt;= A.length &lt;= 10000</code></li>
	<li><code>1 &lt;= A[i] &lt;= 10^6</code></li>
</ol>
</div>
</div>
</div>
</div> instead-->
<p>给定由一些正数（代表长度）组成的数组 <code>A</code>，返回由其中三个长度组成的、<strong>面积不为零</strong>的三角形的最大周长。</p>

<p>如果不能形成任何面积不为零的三角形，返回&nbsp;<code>0</code>。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[2,1,2]
<strong>输出：</strong>5
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[1,2,1]
<strong>输出：</strong>0
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>[3,2,3,4]
<strong>输出：</strong>10
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>[3,6,2,3]
<strong>输出：</strong>8
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>3 &lt;= A.length &lt;= 10000</code></li>
	<li><code>1 &lt;= A[i] &lt;= 10^6</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 24 ms

```java
class Solution {
    public int largestPerimeter(int[] A) {
        Arrays.sort(A);
        for (int i = A.length - 3; i >= 0; --i)
            if (A[i] + A[i+1] > A[i+2])
                return A[i] + A[i+1] + A[i+2];
        return 0;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-perimeter-triangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-perimeter-triangle/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-perimeter-triangle/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-perimeter-triangle/)

[回到目录](../README.md)