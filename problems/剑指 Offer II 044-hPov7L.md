# 剑指 Offer II 044. hPov7L | 二叉树每层的最大值

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一棵二叉树的根节点&nbsp;<code>root</code> ，请找出该二叉树中每一层的最大值。</p>

<p>&nbsp;</p>

<p><strong>示例1：</strong></p>

<pre>
<strong>输入: </strong>root = [1,3,2,5,3,null,9]
<strong>输出: </strong>[1,3,9]
<strong>解释:</strong>
          1
         / \
        3   2
       / \   \  
      5   3   9 
</pre>

<p><strong>示例2：</strong></p>

<pre>
<strong>输入: </strong>root = [1,2,3]
<strong>输出: </strong>[1,3]
<strong>解释:</strong>
          1
         / \
        2   3
</pre>

<p><strong>示例3：</strong></p>

<pre>
<strong>输入: </strong>root = [1]
<strong>输出: </strong>[1]
</pre>

<p><strong>示例4：</strong></p>

<pre>
<strong>输入: </strong>root = [1,null,2]
<strong>输出: </strong>[1,2]
<strong>解释:</strong>      
&nbsp;          1 
&nbsp;           \
&nbsp;            2     
</pre>

<p><strong>示例5：</strong></p>

<pre>
<strong>输入: </strong>root = []
<strong>输出: </strong>[]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>二叉树的节点个数的范围是 <code>[0,10<sup>4</sup>]</code></li>
	<li><meta charset="UTF-8" /><code>-2<sup>31</sup>&nbsp;&lt;= Node.val &lt;= 2<sup>31</sup>&nbsp;- 1</code></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 515&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/find-largest-value-in-each-tree-row/">https://leetcode-cn.com/problems/find-largest-value-in-each-tree-row/</a></p>




## Solution

Language: **java**  /  Runtime: 2 ms

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
    public List<Integer> largestValues(TreeNode root) {
        List<Integer>list=new ArrayList<Integer>();
        if(root==null)return list;
        Queue<TreeNode>queue=new LinkedList<TreeNode>();
        TreeNode p=root;
        queue.offer(root);
        while(!queue.isEmpty()) {
            int size=queue.size();
            int maxSum=Integer.MIN_VALUE;
            for(int i=0;i<size;i++) {
                TreeNode q=queue.poll();
                maxSum=Math.max(maxSum, q.val);
                if(q.left!=null)queue.offer(q.left);
                if(q.right!=null)queue.offer(q.right);
            }
            list.add(maxSum);
        }
        return list;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/hPov7L/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/hPov7L/description/)

Solution: [LeetCode](https://leetcode.com/articles/hPov7L/)  /  [LeetCode中国](https://leetcode-cn.com/articles/hPov7L/)

[回到目录](../README.md)