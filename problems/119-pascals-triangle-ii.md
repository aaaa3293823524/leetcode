# 119. pascals-triangle-ii | 杨辉三角 II

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>rowIndex</code>, return the <code>rowIndex<sup>th</sup></code>&nbsp;row of the Pascal&#39;s triangle.</p>

<p>Notice&nbsp;that the row index starts from&nbsp;<strong>0</strong>.</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" /><br />
<small>In Pascal&#39;s triangle, each number is the sum of the two numbers directly above it.</small></p>

<p><strong>Follow up:</strong></p>

<p>Could you optimize your algorithm to use only <em>O</em>(<em>k</em>) extra space?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> rowIndex = 3
<strong>Output:</strong> [1,3,3,1]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> rowIndex = 0
<strong>Output:</strong> [1]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> rowIndex = 1
<strong>Output:</strong> [1,1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;=&nbsp;rowIndex &lt;= 40</code></li>
</ul>
 instead-->
<p>给定一个非负索引&nbsp;<em>k</em>，其中 <em>k</em>&nbsp;&le;&nbsp;33，返回杨辉三角的第 <em>k </em>行。</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif"></p>

<p><small>在杨辉三角中，每个数是它左上方和右上方的数的和。</small></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong> [1,3,3,1]
</pre>

<p><strong>进阶：</strong></p>

<p>你可以优化你的算法到 <em>O</em>(<em>k</em>) 空间复杂度吗？</p>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
         List<List<Integer>> triangle = new ArrayList<List<Integer>>();

        // First base case; if user requests zero rows, they get zero rows.
       

        // Second base case; first row is always [1].
        triangle.add(new ArrayList<>());
        triangle.get(0).add(1);
         if (rowIndex == 0) {
            return triangle.get(0);
        }
        for (int rowNum = 1; rowNum < rowIndex+1; rowNum++) {
            List<Integer> row = new ArrayList<>();
            List<Integer> prevRow = triangle.get(rowNum-1);

            // The first row element is always 1.
            row.add(1);

            // Each triangle element (other than the first and last of each row)
            // is equal to the sum of the elements above-and-to-the-left and
            // above-and-to-the-right.
            for (int j = 1; j < rowNum; j++) {
                row.add(prevRow.get(j-1) + prevRow.get(j));
            }

            // The last row element is always 1.
            row.add(1);

            triangle.add(row);
            
        }
        return triangle.get(rowIndex);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/pascals-triangle-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pascals-triangle-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/pascals-triangle-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/pascals-triangle-ii/)

[回到目录](../README.md)