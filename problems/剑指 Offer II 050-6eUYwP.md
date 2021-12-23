# 剑指 Offer II 050. 6eUYwP | 向下的路径节点之和

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个二叉树的根节点 <code>root</code>&nbsp;，和一个整数 <code>targetSum</code> ，求该二叉树里节点值之和等于 <code>targetSum</code> 的 <strong>路径</strong> 的数目。</p>

<p><strong>路径</strong> 不需要从根节点开始，也不需要在叶子节点结束，但是路径方向必须是向下的（只能从父节点到子节点）。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img src="https://assets.leetcode.com/uploads/2021/04/09/pathsum3-1-tree.jpg" style="width: 452px; " /></p>

<pre>
<strong>输入：</strong>root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8
<strong>输出：</strong>3
<strong>解释：</strong>和等于 8 的路径有 3 条，如图所示。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
<strong>输出：</strong>3
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li>二叉树的节点个数的范围是 <code>[0,1000]</code></li>
	<li><meta charset="UTF-8" /><code>-10<sup><span style="font-size: 9.449999809265137px;">9</span></sup>&nbsp;&lt;= Node.val &lt;= 10<sup><span style="font-size: 9.449999809265137px;">9</span></sup></code>&nbsp;</li>
	<li><code>-1000&nbsp;&lt;= targetSum&nbsp;&lt;= 1000</code>&nbsp;</li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 437&nbsp;题相同：<a href="https://leetcode-cn.com/problems/path-sum-iii/">https://leetcode-cn.com/problems/path-sum-iii/</a></p>




## Solution

Language: **java**  /  Runtime: 2488 ms

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
    int res=0;
    public int pathSum(TreeNode root, int targetSum) {
        if(root==null)return 0;
        HashMap<Integer,Integer>map=new HashMap<>();
        map.put(0,1);
        dfs(root,0,targetSum,map);
        return res;
    }
    public int  dfs(TreeNode root,int preSum,int targetSum,HashMap<Integer,Integer>map){
        if(map.getOrDefault(root.val+preSum-targetSum,0)>0)res+=map.getOrDefault(root.val+preSum-targetSum,0);
        if (root==null)return 0;
        //int res=0;
        //System.out.println("1:  "+root.val+"  2:  "+preSum+" 3:  "+targetSum);
        //System.out.println(root.val+preSum-targetSum);
        for(int t:map.values()){
            System.out.print(t+" ");
        }
        //System.out.println();
        //if(map.getOrDefault(root.val+preSum-targetSum,0)>0)res++;
        if(root.left!=null){
            map.put(preSum+root.val,map.getOrDefault(preSum+root.val,0)+1);
            dfs(root.left,preSum+root.val,targetSum,map);
            map.put(preSum+root.val,map.getOrDefault(preSum+root.val,0)-1);
        }
        if(root.right!=null){
            map.put(preSum+root.val,map.getOrDefault(preSum+root.val,0)+1);
            dfs(root.right,preSum+root.val,targetSum,map);
            map.put(preSum+root.val,map.getOrDefault(preSum+root.val,0)-1);
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/6eUYwP/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/6eUYwP/description/)

Solution: [LeetCode](https://leetcode.com/articles/6eUYwP/)  /  [LeetCode中国](https://leetcode-cn.com/articles/6eUYwP/)

[回到目录](../README.md)