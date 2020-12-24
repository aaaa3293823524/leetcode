# 986. interval-list-intersections | 区间列表的交集

## Question description

<!--If you want to use the English description, use <p>Given two lists&nbsp;of <strong>closed</strong> intervals, each list of intervals is pairwise disjoint and in sorted order.</p>

<p>Return the intersection of these two interval lists.</p>

<p><em>(Formally, a closed interval <code>[a, b]</code> (with <code>a &lt;= b</code>) denotes&nbsp;the set of real numbers <code>x</code> with <code>a &lt;= x &lt;= b</code>.&nbsp; The&nbsp;intersection of two closed intervals is a set of real numbers that is either empty, or can be represented as a closed interval.&nbsp; For example, the intersection of [1, 3] and [2, 4] is [2, 3].)</em></p>

<div>
<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/01/30/interval1.png" style="width: 506px; height: 140px;" /></strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-1-1">[[0,2],[5,10],[13,23],[24,25]]</span>, B = <span id="example-input-1-2">[[1,5],[8,12],[15,24],[25,26]]</span>
<strong>Output: </strong><span id="example-output-1">[[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>0 &lt;= A.length &lt; 1000</code></li>
	<li><code>0 &lt;= B.length &lt; 1000</code></li>
	<li><code>0 &lt;= A[i].start, A[i].end, B[i].start, B[i].end &lt; 10^9</code></li>
</ol>
</div>
 instead-->
<p>给定两个由一些<strong> 闭区间 </strong>组成的列表，每个区间列表都是成对不相交的，并且已经排序。</p>

<p>返回这两个区间列表的交集。</p>

<p><em>（形式上，闭区间&nbsp;<code>[a, b]</code>（其中&nbsp;<code>a &lt;= b</code>）表示实数&nbsp;<code>x</code>&nbsp;的集合，而&nbsp;<code>a &lt;= x &lt;= b</code>。两个闭区间的交集是一组实数，要么为空集，要么为闭区间。例如，[1, 3] 和 [2, 4] 的交集为 [2, 3]。）</em></p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/02/interval1.png" style="height: 140px; width: 506px;"></strong></p>

<pre><strong>输入：</strong>A = [[0,2],[5,10],[13,23],[24,25]], B = [[1,5],[8,12],[15,24],[25,26]]
<strong>输出：</strong>[[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>0 &lt;= A.length &lt; 1000</code></li>
	<li><code>0 &lt;= B.length &lt; 1000</code></li>
	<li><code>0 &lt;= A[i].start, A[i].end, B[i].start, B[i].end &lt; 10^9</code></li>
</ol>


## Note

归并区间  很巧妙


## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
  public int[][] intervalIntersection(int[][] A, int[][] B) {
    List<int[]> ans = new ArrayList();
    int i = 0, j = 0;

    while (i < A.length && j < B.length) {
      // Let's check if A[i] intersects B[j].
      // lo - the startpoint of the intersection
      // hi - the endpoint of the intersection
      int lo = Math.max(A[i][0], B[j][0]);
      int hi = Math.min(A[i][1], B[j][1]);
      if (lo <= hi)
        ans.add(new int[]{lo, hi});

      // Remove the interval with the smallest endpoint
      if (A[i][1] < B[j][1])
        i++;
      else
        j++;
    }

    return ans.toArray(new int[ans.size()][]);
  }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/interval-list-intersections/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/interval-list-intersections/description/)

Solution: [LeetCode](https://leetcode.com/articles/interval-list-intersections/)  /  [LeetCode中国](https://leetcode-cn.com/articles/interval-list-intersections/)

[回到目录](../README.md)