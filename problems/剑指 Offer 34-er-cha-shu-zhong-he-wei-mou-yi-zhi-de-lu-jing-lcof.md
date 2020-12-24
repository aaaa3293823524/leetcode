# 剑指 Offer 34. er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof | 二叉树中和为某一值的路径

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>输入一棵二叉树和一个整数，打印出二叉树中节点值的和为输入整数的所有路径。从树的根节点开始往下一直到叶节点所经过的节点形成一条路径。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong><br>
给定如下二叉树，以及目标和&nbsp;<code>sum = 22</code>，</p>

<pre>              <strong>5</strong>
             / \
            <strong>4</strong>   <strong>8</strong>
           /   / \
          <strong>11</strong>  13  <strong>4</strong>
         /  \    / \
        7    <strong>2</strong>  <strong>5</strong>   1
</pre>

<p>返回:</p>

<pre>[
   [5,4,11,2],
   [5,8,4,5]
]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>节点总数 &lt;= 10000</code></li>
</ol>

<p>注意：本题与主站 113&nbsp;题相同：<a href="https://leetcode-cn.com/problems/path-sum-ii/">https://leetcode-cn.com/problems/path-sum-ii/</a></p>




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
    LinkedList<List<Integer>> res = new LinkedList<>();
    LinkedList<Integer> path = new LinkedList<>(); 
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        recur(root, sum);
        return res;
    }
    void recur(TreeNode root, int tar) {
        if(root == null) return;
        path.add(root.val);
        tar -= root.val;
        if(tar == 0 && root.left == null && root.right == null)
            res.add(new LinkedList(path));
        recur(root.left, tar);
        recur(root.right, tar);
        path.removeLast();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

[回到目录](../README.md)