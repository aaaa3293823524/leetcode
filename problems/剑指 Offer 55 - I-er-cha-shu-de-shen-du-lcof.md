# 剑指 Offer 55 - I. er-cha-shu-de-shen-du-lcof | 二叉树的深度

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。</p>

<p>例如：</p>

<p>给定二叉树 <code>[3,9,20,null,null,15,7]</code>，</p>

<pre>    3
   / \
  9  20
    /  \
   15   7</pre>

<p>返回它的最大深度&nbsp;3 。</p>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>节点总数 &lt;= 10000</code></li>
</ol>

<p>注意：本题与主站 104&nbsp;题相同：<a href="https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/">https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/</a></p>


## Note

层序遍历



左右子树最大值加1


## Solution

Language: **java**  /  Runtime: 1 ms

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
    public int maxDepth(TreeNode root) {
        Stack<TreeNode>stack=new Stack<>();
        Queue<TreeNode>queue=new LinkedList<>();
        if(root!=null)queue.offer(root);
        int count=0;
        while (!queue.isEmpty()){
            int c=queue.size();
            count++;
            for(int i=0;i<c;i++) {
                TreeNode t = queue.poll();
                if (t.left != null) {
                    queue.offer(t.left);
                }
                if (t.right != null) {
                    queue.offer(t.right);
                }
            }
        }
        return count;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/er-cha-shu-de-shen-du-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/er-cha-shu-de-shen-du-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/er-cha-shu-de-shen-du-lcof/)

[回到目录](../README.md)