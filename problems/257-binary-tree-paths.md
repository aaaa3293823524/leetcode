# 257. binary-tree-paths | 二叉树的所有路径

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, return all root-to-leaf paths.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>

   1
 /   \
2     3
 \
  5

<strong>Output:</strong> [&quot;1-&gt;2-&gt;5&quot;, &quot;1-&gt;3&quot;]

<strong>Explanation:</strong> All root-to-leaf paths are: 1-&gt;2-&gt;5, 1-&gt;3
</pre> instead-->
<p>给定一个二叉树，返回所有从根节点到叶子节点的路径。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>

   1
 /   \
2     3
 \
  5

<strong>输出:</strong> [&quot;1-&gt;2-&gt;5&quot;, &quot;1-&gt;3&quot;]

<strong>解释:</strong> 所有根节点到叶子节点的路径为: 1-&gt;2-&gt;5, 1-&gt;3</pre>




## Solution

Language: **python3**  /  Runtime: 52 ms

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def binaryTreePaths(self, root):
        """
        :type root: TreeNode
        :rtype: List[str]
        """
        if not root:
            return []
        
        paths = []
        stack = [(root, str(root.val))]
        while stack:
            node, path = stack.pop()
            if not node.left and not node.right:
                paths.append(path)
            if node.left:
                stack.append((node.left, path + '->' + str(node.left.val)))
            if node.right:
                stack.append((node.right, path + '->' + str(node.right.val)))
        
        return paths


```

Language: **java**  /  Runtime: 4 ms

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public void construct_paths(TreeNode root, String path, LinkedList<String> paths) {
        if (root != null) {
            path += Integer.toString(root.val);
            if ((root.left == null) && (root.right == null))  // 当前节点是叶子节点
                paths.add(path);  // 把路径加入到答案中
            else {
                path += "->";  // 当前节点不是叶子节点，继续递归遍历
                construct_paths(root.left, path, paths);
                construct_paths(root.right, path, paths);
            }
        }
    }

    public List<String> binaryTreePaths(TreeNode root) {
        LinkedList<String> paths = new LinkedList();
        construct_paths(root, "", paths);
        return paths;
    }
}



```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-paths/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-paths/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-paths/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-paths/)

[回到目录](../README.md)