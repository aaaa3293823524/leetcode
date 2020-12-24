# 113. path-sum-ii | 路径总和 II

## Question description

<!--If you want to use the English description, use <p>Given a binary tree and a sum, find all root-to-leaf paths where each path&#39;s sum equals the given sum.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<p>Given the below binary tree and <code>sum = 22</code>,</p>

<pre>
      <strong>5</strong>
     <strong>/ \</strong>
    <strong>4   8</strong>
   <strong>/</strong>   / <strong>\</strong>
  <strong>11</strong>  13  <strong>4</strong>
 /  <strong>\</strong>    <strong>/</strong> \
7    <strong>2</strong>  <strong>5</strong>   1
</pre>

<p>Return:</p>

<pre>
[
   [5,4,11,2],
   [5,8,4,5]
]
</pre>
 instead-->
<p>给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例:</strong><br>
给定如下二叉树，以及目标和&nbsp;<code>sum = 22</code>，</p>

<pre>              <strong>5</strong>
             / \
            <strong>4</strong>   <strong>8</strong>
           /   / \
          <strong>11</strong>  13  <strong>4</strong>
         /  \    / \
        7    <strong>2</strong>  <strong>5</strong>   1
</pre>

<p>返回:</p>

<pre>[
   [5,4,11,2],
   [5,8,4,5]
]
</pre>


## Note

1 深度优先搜索



2 广度优先搜索


## Solution

Language: **python3**  /  Runtime: 72 ms

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None


#  深度优先搜索
class Solution:
    def pathSum(self, root: TreeNode, total: int) -> List[List[int]]:
        ret = list()
        path = list()
        
        def dfs(root: TreeNode, total: int):
            if not root:
                return
            path.append(root.val)
            total -= root.val
            if not root.left and not root.right and total == 0:
                ret.append(path[:])
            dfs(root.left, total)
            dfs(root.right, total)
            path.pop()
        
        dfs(root, total)
        return ret


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/path-sum-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/path-sum-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/path-sum-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/path-sum-ii/)

[回到目录](../README.md)