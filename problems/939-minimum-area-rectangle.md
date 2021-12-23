# 939. minimum-area-rectangle | 最小面积矩形

## Question description

<!--If you want to use the English description, use <p>You are given an array of points in the <strong>X-Y</strong> plane <code>points</code> where <code>points[i] = [x<sub>i</sub>, y<sub>i</sub>]</code>.</p>

<p>Return <em>the minimum area of a rectangle formed from these points, with sides parallel to the X and Y axes</em>. If there is not any such rectangle, return <code>0</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/08/03/rec1.JPG" style="width: 500px; height: 447px;" />
<pre>
<strong>Input:</strong> points = [[1,1],[1,3],[3,1],[3,3],[2,2]]
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/08/03/rec2.JPG" style="width: 500px; height: 477px;" />
<pre>
<strong>Input:</strong> points = [[1,1],[1,3],[3,1],[3,3],[4,1],[4,3]]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= points.length &lt;= 500</code></li>
	<li><code>points[i].length == 2</code></li>
	<li><code>0 &lt;= x<sub>i</sub>, y<sub>i</sub> &lt;= 4 * 10<sup>4</sup></code></li>
	<li>All the given points are <strong>unique</strong>.</li>
</ul>
 instead-->
<p>给定在 xy 平面上的一组点，确定由这些点组成的矩形的最小面积，其中矩形的边平行于 x 轴和 y 轴。</p>

<p>如果没有任何矩形，就返回 0。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[[1,1],[1,3],[3,1],[3,3],[2,2]]
<strong>输出：</strong>4
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[[1,1],[1,3],[3,1],[3,3],[4,1],[4,3]]
<strong>输出：</strong>2
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= points.length &lt;= 500</code></li>
	<li><code>0 &lt;=&nbsp;points[i][0] &lt;=&nbsp;40000</code></li>
	<li><code>0 &lt;=&nbsp;points[i][1] &lt;=&nbsp;40000</code></li>
	<li>所有的点都是不同的。</li>
</ol>


## Note

按列排序   同一列的两个点 (x, y1) 和 (x, y2)，我们找出它作为右边界的最小的矩形


## Solution

Language: **java**  /  Runtime: 200 ms

```java
class Solution {
    public int minAreaRect(int[][] points) {
        Map<Integer, List<Integer>> rows = new TreeMap();
        for (int[] point: points) {
            int x = point[0], y = point[1];
            rows.computeIfAbsent(x, z-> new ArrayList()).add(y);
        }

        int ans = Integer.MAX_VALUE;
        Map<Integer, Integer> lastx = new HashMap();
        for (int x: rows.keySet()) {
            List<Integer> row = rows.get(x);
            Collections.sort(row);
            for (int i = 0; i < row.size(); ++i)
                for (int j = i+1; j < row.size(); ++j) {
                    int y1 = row.get(i), y2 = row.get(j);
                    int code = 40001 * y1 + y2;
                    if (lastx.containsKey(code))
                        ans = Math.min(ans, (x - lastx.get(code)) * (y2-y1));
                    lastx.put(code, x);
                }
        }

        return ans < Integer.MAX_VALUE ? ans : 0;
    }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-area-rectangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-area-rectangle/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-area-rectangle/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-area-rectangle/)

[回到目录](../README.md)