# 637. average-of-levels-in-binary-tree | 二叉树的层平均值

## Question description

<!--If you want to use the English description, use Given the <code>root</code> of a binary tree, return <em>the average value of the nodes on each level in the form of an array</em>. Answers within <code>10<sup>-5</sup></code> of the actual answer will be accepted.
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/09/avg1-tree.jpg" style="width: 277px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> [3.00000,14.50000,11.00000]
Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/09/avg2-tree.jpg" style="width: 292px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [3,9,20,15,7]
<strong>Output:</strong> [3.00000,14.50000,11.00000]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>-2<sup>31</sup> &lt;= Node.val &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给定一个非空二叉树, 返回一个由每层节点平均值组成的数组。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>
    3
   / \
  9  20
    /  \
   15   7
<strong>输出：</strong>[3, 14.5, 11]
<strong>解释：</strong>
第 0 层的平均值是 3 ,  第1层是 14.5 , 第2层是 11 。因此返回 [3, 14.5, 11] 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>节点值的范围在32位有符号整数范围内。</li>
</ul>




## Solution

Language: **python3**  /  Runtime: 80 ms

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def averageOfLevels(self, root: TreeNode) -> List[float]:
        ans = [root]
        target = []
        while ans:
            n = len(ans)
            tmp,sum_= [],0
            for i in range(n):
                r =ans.pop(0)
                sum_+=r.val
                if r.left:
                    ans.append(r.left)
                if r.right:
                    ans.append(r.right)
            target.append(sum_/(i+1))
        return target


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/average-of-levels-in-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/average-of-levels-in-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/average-of-levels-in-binary-tree/)

[回到目录](../README.md)