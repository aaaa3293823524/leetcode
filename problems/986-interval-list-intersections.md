# 986. interval-list-intersections | 区间列表的交集

## Question description

<!--If you want to use the English description, use <p>You are given two lists of closed intervals, <code>firstList</code> and <code>secondList</code>, where <code>firstList[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> and <code>secondList[j] = [start<sub>j</sub>, end<sub>j</sub>]</code>. Each list of intervals is pairwise <strong>disjoint</strong> and in <strong>sorted order</strong>.</p>

<p>Return <em>the intersection of these two interval lists</em>.</p>

<p>A <strong>closed interval</strong> <code>[a, b]</code> (with <code>a &lt;= b</code>) denotes the set of real numbers <code>x</code> with <code>a &lt;= x &lt;= b</code>.</p>

<p>The <strong>intersection</strong> of two closed intervals is a set of real numbers that are either empty or represented as a closed interval. For example, the intersection of <code>[1, 3]</code> and <code>[2, 4]</code> is <code>[2, 3]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/30/interval1.png" style="width: 700px; height: 194px;" />
<pre>
<strong>Input:</strong> firstList = [[0,2],[5,10],[13,23],[24,25]], secondList = [[1,5],[8,12],[15,24],[25,26]]
<strong>Output:</strong> [[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> firstList = [[1,3],[5,9]], secondList = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> firstList = [], secondList = [[4,8],[10,12]]
<strong>Output:</strong> []
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> firstList = [[1,7]], secondList = [[3,10]]
<strong>Output:</strong> [[3,7]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= firstList.length, secondList.length &lt;= 1000</code></li>
	<li><code>firstList.length + secondList.length &gt;= 1</code></li>
	<li><code>0 &lt;= start<sub>i</sub> &lt; end<sub>i</sub> &lt;= 10<sup>9</sup></code></li>
	<li><code>end<sub>i</sub> &lt; start<sub>i+1</sub></code></li>
	<li><code>0 &lt;= start<sub>j</sub> &lt; end<sub>j</sub> &lt;= 10<sup>9</sup> </code></li>
	<li><code>end<sub>j</sub> &lt; start<sub>j+1</sub></code></li>
</ul>
 instead-->
<p>给定两个由一些<strong> 闭区间 </strong>组成的列表，<code>firstList</code> 和 <code>secondList</code> ，其中 <code>firstList[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> 而 <code>secondList[j] = [start<sub>j</sub>, end<sub>j</sub>]</code> 。每个区间列表都是成对 <strong>不相交</strong> 的，并且 <strong>已经排序</strong> 。</p>

<p>返回这 <strong>两个区间列表的交集</strong> 。</p>

<p>形式上，<strong>闭区间</strong> <code>[a, b]</code>（其中 <code>a <= b</code>）表示实数 <code>x</code> 的集合，而 <code>a <= x <= b</code> 。</p>

<p>两个闭区间的 <strong>交集</strong> 是一组实数，要么为空集，要么为闭区间。例如，<code>[1, 3]</code> 和 <code>[2, 4]</code> 的交集为 <code>[2, 3]</code> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/30/interval1.png" style="width: 700px; height: 194px;" />
<pre>
<strong>输入：</strong>firstList = [[0,2],[5,10],[13,23],[24,25]], secondList = [[1,5],[8,12],[15,24],[25,26]]
<strong>输出：</strong>[[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>firstList = [[1,3],[5,9]], secondList = []
<strong>输出：</strong>[]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>firstList = [], secondList = [[4,8],[10,12]]
<strong>输出：</strong>[]
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>firstList = [[1,7]], secondList = [[3,10]]
<strong>输出：</strong>[[3,7]]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= firstList.length, secondList.length <= 1000</code></li>
	<li><code>firstList.length + secondList.length >= 1</code></li>
	<li><code>0 <= start<sub>i</sub> < end<sub>i</sub> <= 10<sup>9</sup></code></li>
	<li><code>end<sub>i</sub> < start<sub>i+1</sub></code></li>
	<li><code>0 <= start<sub>j</sub> < end<sub>j</sub> <= 10<sup>9</sup> </code></li>
	<li><code>end<sub>j</sub> < start<sub>j+1</sub></code></li>
</ul>


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