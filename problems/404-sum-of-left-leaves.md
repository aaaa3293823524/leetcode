# 404. sum-of-left-leaves | 左叶子之和

## Question description

<!--If you want to use the English description, use <p>Given the <code>root</code> of a binary tree, return the sum of all left leaves.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/08/leftsum-tree.jpg" style="width: 277px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> 24
<strong>Explanation:</strong> There are two left leaves in the binary tree, with values 9 and 15 respectively.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [1]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 1000]</code>.</li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
</ul>
 instead-->
<p>计算给定二叉树的所有左叶子之和。</p>

<p><strong>示例：</strong></p>

<pre>
    3
   / \
  9  20
    /  \
   15   7

在这个二叉树中，有两个左叶子，分别是 9 和 15，所以返回 24</pre>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int sumOfLeftLeaves(TreeNode root) {
        int sum=0;
        if(root==null)return root.val;
        Queue<TreeNode>queue=new LinkedList<TreeNode>();
        Queue<String>q=new LinkedList<String>();
        queue.offer(root);
        q.offer("root");
        while(!queue.isEmpty()) {
            TreeNode node=queue.poll();
            String string=q.poll();
            //System.out.println(string+" ");
            if(node.left==null&&node.right==null&&string.equals("l")) {
                sum+=node.val;
            }
            if(node.left!=null) {
                queue.offer(node.left);
                q.offer("l");
            }
            if(node.right!=null) {
                queue.offer(node.right);
                q.offer("r");
            }
        }
        return sum;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-left-leaves/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-left-leaves/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-left-leaves/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-left-leaves/)

[回到目录](../README.md)