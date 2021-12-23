# 剑指 Offer 04. er-wei-shu-zu-zhong-de-cha-zhao-lcof | 二维数组中的查找

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。</p>

<p> </p>

<p><strong>示例:</strong></p>

<p>现有矩阵 matrix 如下：</p>

<pre>
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
</pre>

<p>给定 target = <code>5</code>，返回 <code>true</code>。</p>

<p>给定 target = <code>20</code>，返回 <code>false</code>。</p>

<p> </p>

<p><strong>限制：</strong></p>

<p><code>0 <= n <= 1000</code></p>

<p><code>0 <= m <= 1000</code></p>

<p> </p>

<p><strong>注意：</strong>本题与主站 240 题相同：<a href="https://leetcode-cn.com/problems/search-a-2d-matrix-ii/">https://leetcode-cn.com/problems/search-a-2d-matrix-ii/</a></p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }
        int rows = matrix.length, columns = matrix[0].length;
        int row = 0, column = columns - 1;
        while (row < rows && column >= 0) {
            int num = matrix[row][column];
            if (num == target) {
                return true;
            } else if (num > target) {
                column--;
            } else {
                row++;
            }
        }
        return false;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)

[回到目录](../README.md)