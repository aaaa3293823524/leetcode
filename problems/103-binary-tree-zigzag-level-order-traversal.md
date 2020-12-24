# 103. binary-tree-zigzag-level-order-traversal | 二叉树的锯齿形层次遍历

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, return the <i>zigzag level order</i> traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).</p>

<p>
For example:<br />
Given binary tree <code>[3,9,20,null,null,15,7]</code>,<br />
<pre>
    3
   / \
  9  20
    /  \
   15   7
</pre>
</p>
<p>
return its zigzag level order traversal as:<br />
<pre>
[
  [3],
  [20,9],
  [15,7]
]
</pre>
</p> instead-->
<p>给定一个二叉树，返回其节点值的锯齿形层次遍历。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。</p>

<p>例如：<br>
给定二叉树&nbsp;<code>[3,9,20,null,null,15,7]</code>,</p>

<pre>    3
   / \
  9  20
    /  \
   15   7
</pre>

<p>返回锯齿形层次遍历如下：</p>

<pre>[
  [3],
  [20,9],
  [15,7]
]
</pre>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null)
            return result;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        // 记录是否反转
        boolean isReverse = false;
        while (!queue.isEmpty()) {
            LinkedList<Integer> oneLevel = new LinkedList<>();
            // 每次都取出一层的所有数据
            int count = queue.size();
            for (int i = 0; i < count; i++) {
                TreeNode node = queue.poll();
                if (!isReverse)
                    oneLevel.add(node.val);
                else
                    oneLevel.addFirst(node.val);
                if (node.left != null)
                    queue.add(node.left);
                if (node.right != null)
                    queue.add(node.right);
            }
            isReverse = !isReverse;
            result.add(oneLevel);
        }
        return result;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-zigzag-level-order-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-zigzag-level-order-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-zigzag-level-order-traversal/)

[回到目录](../README.md)