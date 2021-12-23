# 剑指 Offer 32 - I. cong-shang-dao-xia-da-yin-er-cha-shu-lcof | 从上到下打印二叉树

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。</p>

<p>&nbsp;</p>

<p>例如:<br>
给定二叉树:&nbsp;<code>[3,9,20,null,null,15,7]</code>,</p>

<pre>    3
   / \
  9  20
    /  \
   15   7
</pre>

<p>返回：</p>

<pre>[3,9,20,15,7]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>节点总数 &lt;= 1000</code></li>
</ol>




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
    public int[] levelOrder(TreeNode root) {
        List<Integer>list=new ArrayList<Integer>();
        Queue<TreeNode>queue=new LinkedList<TreeNode>();
        queue.offer(root);
        int count=0;
        while(!queue.isEmpty()) {
            TreeNode t=queue.poll();
            if(t!=null)list.add(t.val);
            else{
                break;
            }
            if(t.left!=null)queue.offer(t.left);
            if(t.right!=null)queue.offer(t.right);
        }
        int[]result=new int[list.size()];
        for(int i=0;i<list.size();i++) {
            result[i]=list.get(i);
        }
        return result;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

[回到目录](../README.md)