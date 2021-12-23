# 剑指 Offer 54. er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof | 二叉搜索树的第k大节点

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>给定一棵二叉搜索树，请找出其中第 <code>k</code> 大的节点的值。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
&nbsp;  2
<strong>输出:</strong> 4</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
<strong>输出:</strong> 4</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li>1 ≤ k ≤ 二叉搜索树元素个数</li>
</ul>




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
    public int kthLargest(TreeNode root, int k) {
        List<Integer>list=new ArrayList<Integer>();
        dfs(root,list);
        return list.get(list.size()-k);
    }
    public void dfs(TreeNode root,List<Integer>list) {
        if(root==null)return;
        dfs(root.left, list);
        list.add(root.val);
        dfs(root.right, list);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

[回到目录](../README.md)