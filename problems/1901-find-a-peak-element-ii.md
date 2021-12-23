# 1901. find-a-peak-element-ii | 找出顶峰元素 II

## Question description

<!--If you want to use the English description, use <p>A <strong>peak</strong> element in a 2D grid is an element that is <strong>strictly greater</strong> than all of its <strong>adjacent </strong>neighbors to the left, right, top, and bottom.</p>

<p>Given a <strong>0-indexed</strong> <code>m x n</code> matrix <code>mat</code> where <strong>no two adjacent cells are equal</strong>, find <strong>any</strong> peak element <code>mat[i][j]</code> and return <em>the length 2 array </em><code>[i,j]</code>.</p>

<p>You may assume that the entire matrix is surrounded by an <strong>outer perimeter</strong> with the value <code>-1</code> in each cell.</p>

<p>You must write an algorithm that runs in <code>O(m log(n))</code> or <code>O(n log(m))</code> time.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/06/08/1.png" style="width: 206px; height: 209px;" /></p>

<pre>
<strong>Input:</strong> mat = [[1,4],[3,2]]
<strong>Output:</strong> [0,1]
<strong>Explanation:</strong>&nbsp;Both 3 and 4 are peak elements so [1,0] and [0,1] are both acceptable answers.
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2021/06/07/3.png" style="width: 254px; height: 257px;" /></strong></p>

<pre>
<strong>Input:</strong> mat = [[10,20,15],[21,30,14],[7,16,32]]
<strong>Output:</strong> [1,1]
<strong>Explanation:</strong>&nbsp;Both 30 and 32 are peak elements so [1,1] and [2,2] are both acceptable answers.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>1 &lt;= mat[i][j] &lt;= 10<sup>5</sup></code></li>
	<li>No two adjacent cells are equal.</li>
</ul>
 instead-->
<p>一个 2D 网格中的 <strong>顶峰元素 </strong>是指那些 <strong>严格大于 </strong>其相邻格子(上、下、左、右)的元素。</p>

<p>给你一个<strong> 从 0 开始编号 </strong>的 <code>m x n</code> 矩阵 <code>mat</code> ，其中任意两个相邻格子的值都<strong> 不相同</strong> 。找出 <strong>任意一个 </strong>顶峰元素 <code>mat[i][j]</code> 并 <strong>返回其位置 </strong><code>[i,j]</code> 。</p>

<p>你可以假设整个矩阵周边环绕着一圈值为 <code>-1</code> 的格子。</p>

<p>要求必须写出时间复杂度为 <code>O(m log(n))</code> 或 <code>O(n log(m))</code> 的算法</p>

<p> </p>

<p> </p>

<p><strong>示例 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/06/08/1.png" style="width: 206px; height: 209px;" /></p>

<pre>
<strong>输入:</strong> mat = [[1,4],[3,2]]
<strong>输出:</strong> [0,1]
<strong>解释:</strong> 3和4都是顶峰元素，所以[1,0]和[0,1]都是可接受的答案。
</pre>

<p><strong>示例 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2021/06/07/3.png" style="width: 254px; height: 257px;" /></strong></p>

<pre>
<strong>输入:</strong> mat = [[10,20,15],[21,30,14],[7,16,32]]
<strong>输出:</strong> [1,1]
<strong>解释:</strong> 30和32都是顶峰元素，所以[1,1]和[2,2]都是可接受的答案。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 <= m, n <= 500</code></li>
	<li><code>1 <= mat[i][j] <= 10<sup>5</sup></code></li>
	<li>任意两个相邻元素均不相等.</li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    // 返回行最大值的列号
    public int maxOfRow(int[][] mat, int row) {
        if (row < 0 || row >= mat.length) {
            return -1;
        }
        int col = 0;
        for (int i = 1; i < mat[row].length; i++) {
            if (mat[row][i] > mat[row][col]) {
                col = i;
            }
        }
        return col;
    }

    public int[] findPeakGrid(int[][] mat) {
        int top = 0;
        int down = mat.length - 1;
        int mid;
        // m1 mid前一行最大值列号，m2:mid最大值列号，m3:mid+1行最大值列号
        int m1, m2, m3;
        int v1, v2, v3; //中间三行对应的最大值
        while (top <= down) {
            mid = (top + down) / 2;
            //System.out.printf("%d %d %d\n",top,mid,down);
            m2 = maxOfRow(mat, mid);
            if (top == down) {
                return new int[]{mid, m2};
            }
            m1 = maxOfRow(mat, mid - 1);
            m3 = maxOfRow(mat, mid + 1);

            v1 = mid - 1 >= 0 ? mat[mid - 1][m1] : -1;
            v2 = mat[mid][m2];
            v3 = mid + 1 < mat.length ? mat[mid + 1][m3] : -1;
            // 中间行最大，直接顶峰
            if (v2 > v3 && v2 > v1) {
                return new int[]{mid, m2};
            }
            // mid-1行最大
            if (v1 > v3 && v1 >= v2) {
                down = mid - 1;
            } else {
                // mid+1行最大
                top = mid + 1;
            }
        }
        return null;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-a-peak-element-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-a-peak-element-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-a-peak-element-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-a-peak-element-ii/)

[回到目录](../README.md)