# 637. average-of-levels-in-binary-tree | 二叉树的层平均值

## Question description

<!--If you want to use the English description, use Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b>
    3
   / \
  9  20
    /  \
   15   7
<b>Output:</b> [3, 14.5, 11]
<b>Explanation:</b>
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>The range of node's value is in the range of 32-bit signed integer.</li>
</ol>
</p> instead-->
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