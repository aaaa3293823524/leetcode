# 剑指 Offer II 051. jC7MId | 节点之和最大的路径

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p><strong>路径</strong> 被定义为一条从树中任意节点出发，沿父节点-子节点连接，达到任意节点的序列。同一个节点在一条路径序列中 <strong>至多出现一次</strong> 。该路径<strong> 至少包含一个 </strong>节点，且不一定经过根节点。</p>

<p><strong>路径和</strong> 是路径中各节点值的总和。</p>

<p>给定一个二叉树的根节点 <code>root</code> ，返回其 <strong>最大路径和</strong>，即所有路径上节点值之和的最大值。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/10/13/exx1.jpg" style="width: 322px; height: 182px;" /></p>

<pre>
<strong>输入：</strong>root = [1,2,3]
<strong>输出：</strong>6
<strong>解释：</strong>最优路径是 2 -&gt; 1 -&gt; 3 ，路径和为 2 + 1 + 3 = 6</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/10/13/exx2.jpg" /></p>

<pre>
<strong>输入：</strong>root = [-10,9,20,null,null,15,7]
<strong>输出：</strong>42
<strong>解释：</strong>最优路径是 15 -&gt; 20 -&gt; 7 ，路径和为 15 + 20 + 7 = 42
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>树中节点数目范围是 <code>[1, 3 * 10<sup>4</sup>]</code></li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 124&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/">https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/</a></p>




## Solution

Language: **cpp**  /  Runtime: 24 ms

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int maxPathSum(TreeNode* root) {
        //因为节点值最小为-1000，即使二叉树中所有节点都是-1000
        //最大路径和就是其中一个节点，即-1000
        int maxSum = -1000;
        dfs(root, maxSum);

        return maxSum;
    }

    int dfs(TreeNode* root, int& maxSum)
    {
        if (root == nullptr) return 0;

        //若当前子树和小于0，则不选当前子树所在的路径，于是取0
        int left = max(0, dfs(root->left, maxSum));
        int right = max(0, dfs(root->right, maxSum));

        //路径同时经过当前节点左右子树的情况
        maxSum = max(maxSum, root->val + left + right);

        //函数的返回值是经过当前节点root并前往其左子树或右子树的路径的节点值之和的最大值
        return root->val + max(left, right);
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/jC7MId/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/jC7MId/description/)

Solution: [LeetCode](https://leetcode.com/articles/jC7MId/)  /  [LeetCode中国](https://leetcode-cn.com/articles/jC7MId/)

[回到目录](../README.md)