# 剑指 Offer 27. er-cha-shu-de-jing-xiang-lcof | 二叉树的镜像

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>请完成一个函数，输入一个二叉树，该函数输出它的镜像。</p>

<p>例如输入：</p>

<p><code>&nbsp; &nbsp; &nbsp;4<br>
&nbsp; &nbsp;/ &nbsp; \<br>
&nbsp; 2 &nbsp; &nbsp; 7<br>
&nbsp;/ \ &nbsp; / \<br>
1 &nbsp; 3 6 &nbsp; 9</code><br>
镜像输出：</p>

<p><code>&nbsp; &nbsp; &nbsp;4<br>
&nbsp; &nbsp;/ &nbsp; \<br>
&nbsp; 7 &nbsp; &nbsp; 2<br>
&nbsp;/ \ &nbsp; / \<br>
9 &nbsp; 6 3&nbsp; &nbsp;1</code></p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>root = [4,2,7,1,3,6,9]
<strong>输出：</strong>[4,7,2,9,6,3,1]
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= 节点个数 &lt;= 1000</code></p>

<p>注意：本题与主站 226 题相同：<a href="https://leetcode-cn.com/problems/invert-binary-tree/">https://leetcode-cn.com/problems/invert-binary-tree/</a></p>




## Solution

Language: **java**  /  Runtime: 0 ms

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
    public TreeNode mirrorTree(TreeNode root) {
        if(root==null)return root;
        TreeNode l=root.left,r=root.right;
        boolean flag=false;
        if(root.left!=null)
        root.right=mirrorTree(l);
        else{
            flag=true;
        }
        if(root.right!=null)
        root.left=mirrorTree(r);
        else{
            root.left=null;
        }
        if(flag)root.right=null;
        //root.right=mirrorTree(l);
        //root.left=mirrorTree(r);
        return root;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/er-cha-shu-de-jing-xiang-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/er-cha-shu-de-jing-xiang-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/er-cha-shu-de-jing-xiang-lcof/)

[回到目录](../README.md)