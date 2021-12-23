# 119. pascals-triangle-ii | 杨辉三角 II

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>rowIndex</code>, return the <code>rowIndex<sup>th</sup></code> (<strong>0-indexed</strong>) row of the <strong>Pascal&#39;s triangle</strong>.</p>

<p>In <strong>Pascal&#39;s triangle</strong>, each number is the sum of the two numbers directly above it as shown:</p>
<img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" style="height:240px; width:260px" />
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
	<li><code>0 &lt;= rowIndex &lt;= 33</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you optimize your algorithm to use only <code>O(rowIndex)</code> extra space?</p>
 instead-->
<p>给定一个非负索引 <code>rowIndex</code>，返回「杨辉三角」的第 <code>rowIndex</code><em> </em>行。</p>

<p><small>在「杨辉三角」中，每个数是它左上方和右上方的数的和。</small></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626927345-DZmfxB-PascalTriangleAnimated2.gif" /></p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> rowIndex = 3
<strong>输出:</strong> [1,3,3,1]
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> rowIndex = 0
<strong>输出:</strong> [1]
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> rowIndex = 1
<strong>输出:</strong> [1,1]
</pre>

<p> </p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>0 <= rowIndex <= 33</code></li>
</ul>

<p> </p>

<p><strong>进阶：</strong></p>

<p>你可以优化你的算法到 <code><em>O</em>(<i>rowIndex</i>)</code> 空间复杂度吗？</p>




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