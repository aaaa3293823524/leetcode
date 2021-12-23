# 102. binary-tree-level-order-traversal | 二叉树的层序遍历

## Question description

<!--If you want to use the English description, use <p>Given the <code>root</code> of a binary tree, return <em>the level order traversal of its nodes&#39; values</em>. (i.e., from left to right, level by level).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg" style="width: 277px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> [[3],[9,20],[15,7]]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [1]
<strong>Output:</strong> [[1]]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 2000]</code>.</li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你一个二叉树，请你返回其按 <strong>层序遍历</strong> 得到的节点值。 （即逐层地，从左到右访问所有节点）。</p>

<p> </p>

<p><strong>示例：</strong><br />
二叉树：<code>[3,9,20,null,null,15,7]</code>,</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7
</pre>

<p>返回其层序遍历结果：</p>

<pre>
[
  [3],
  [9,20],
  [15,7]
]
</pre>




## Solution

Language: **java**  /  Runtime: 3 ms

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
  public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> levels = new ArrayList<List<Integer>>();
    if (root == null) return levels;

    Queue<TreeNode> queue = new LinkedList<TreeNode>();
    queue.add(root);
    int level = 0;
    while ( !queue.isEmpty() ) {
      // start the current level
      levels.add(new ArrayList<Integer>());

      // number of elements in the current level
      int level_length = queue.size();
      for(int i = 0; i < level_length; ++i) {
        TreeNode node = queue.remove();

        // fulfill the current level
        levels.get(level).add(node.val);

        // add child nodes of the current level
        // in the queue for the next level
        if (node.left != null) queue.add(node.left);
        if (node.right != null) queue.add(node.right);
      }
      // go to next level
      level++;
    }
    return levels;
  }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-level-order-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-level-order-traversal/)

[回到目录](../README.md)