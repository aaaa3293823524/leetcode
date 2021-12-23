# 剑指 Offer II 056. opLdQZ | 二叉搜索树中两个节点之和

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p> instead-->
<p>给定一个二叉搜索树的 <strong>根节点</strong> <code>root</code>&nbsp;和一个整数 <code>k</code> , 请判断该二叉搜索树中是否存在两个节点它们的值之和等于 <code>k</code> 。假设二叉搜索树中节点的值均唯一。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入: </strong>root =<strong> </strong>[8,6,10,5,7,9,11], k = 12
<strong>输出: </strong>true
<strong>解释: </strong>节点 5 和节点 7 之和等于 12
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入: </strong>root =<strong> </strong>[8,6,10,5,7,9,11], k = 22
<strong>输出: </strong>false
<strong>解释: </strong>不存在两个节点值之和为 22 的节点
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>二叉树的节点个数的范围是&nbsp;&nbsp;<code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>4</sup>&nbsp;&lt;= Node.val &lt;= 10<sup>4</sup></code></li>
	<li><code>root</code>&nbsp;为二叉搜索树</li>
	<li><code>-10<sup>5</sup>&nbsp;&lt;= k &lt;= 10<sup>5</sup></code></li>
</ul>

<p>&nbsp;</p>

<p>注意：本题与主站 653 题相同：&nbsp;<a href="https://leetcode-cn.com/problems/two-sum-iv-input-is-a-bst/">https://leetcode-cn.com/problems/two-sum-iv-input-is-a-bst/</a></p>




## Solution

Language: **java**  /  Runtime: 4 ms

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
    boolean flag=false;
    public boolean findTarget(TreeNode root, int k) {
        HashMap<Integer,Integer>map=new HashMap<>();
        //map.put(0,1);
        dfs(root,k,map);
        //boolean flag=dfs(root,k,map);
        //dfs(root,k,map);
        // for(int t:map.keySet()){
        //     System.out.println("mm: "+t+"  :  "+map.getOrDefault(t,0));
        // }
        //boolean flag=false;
        return flag;
    }
    public void dfs(TreeNode root, int k,HashMap<Integer,Integer>map){
        if(root==null)return;
        //System.out.println("{}: "+k+"  :  {}"+root.val);
        // for(int t:map.keySet()){
        //     System.out.println("mm: "+t+"  :  "+map.getOrDefault(t,0));
        // }
        if(map.containsKey(k-root.val)){
            flag=true;
            return;
        }
        map.put(root.val,map.getOrDefault(root.val,0)+1);

        // if(root==null)return false;
        // if(map.containsKey(k-root.val))return true;
        dfs(root.left,k,map);
        //System.out.println(root.val);
        //map.put(root.val,map.getOrDefault(root.val,0)+1);
        dfs(root.right,k,map);
        //return false;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/opLdQZ/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/opLdQZ/description/)

Solution: [LeetCode](https://leetcode.com/articles/opLdQZ/)  /  [LeetCode中国](https://leetcode-cn.com/articles/opLdQZ/)

[回到目录](../README.md)