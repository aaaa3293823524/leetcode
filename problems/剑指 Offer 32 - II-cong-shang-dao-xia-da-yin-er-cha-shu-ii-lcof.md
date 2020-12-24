# 剑指 Offer 32 - II. cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof | 从上到下打印二叉树 II

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。</p>

<p>&nbsp;</p>

<p>例如:<br>
给定二叉树:&nbsp;<code>[3,9,20,null,null,15,7]</code>,</p>

<pre>    3
   / \
  9  20
    /  \
   15   7
</pre>

<p>返回其层次遍历结果：</p>

<pre>[
  [3],
  [9,20],
  [15,7]
]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>节点总数 &lt;= 1000</code></li>
</ol>

<p>注意：本题与主站 102 题相同：<a href="https://leetcode-cn.com/problems/binary-tree-level-order-traversal/">https://leetcode-cn.com/problems/binary-tree-level-order-traversal/</a></p>




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
    public List<List<Integer>> levelOrder(TreeNode root) {
//        if(root==null)return new ArrayList<List<Integer>>();
        List<Integer>list1=new ArrayList<Integer>();
        List<List<Integer>>list2=new ArrayList<List<Integer>>();
        Queue<TreeNode>queue=new LinkedList<TreeNode>();
        if(root!=null)queue.offer(root);
        while(!queue.isEmpty()) {
            int s=queue.size();
            list1.clear();
            for(int i=0;i<s;i++) {
                TreeNode t=queue.poll();
                list1.add(t.val);
                if(t.left!=null)queue.add(t.left);
                if(t.right!=null)queue.add(t.right);
            }
            list2.add(new ArrayList(list1));
        }
        return list2;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

[回到目录](../README.md)