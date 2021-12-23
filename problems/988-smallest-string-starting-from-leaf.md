# 988. smallest-string-starting-from-leaf | 从叶结点开始的最小字符串

## Question description

<!--If you want to use the English description, use <p>You are given the <code>root</code> of a binary tree where each node has a value in the range <code>[0, 25]</code> representing the letters <code>&#39;a&#39;</code> to <code>&#39;z&#39;</code>.</p>

<p>Return <em>the <strong>lexicographically smallest</strong> string that starts at a leaf of this tree and ends at the root</em>.</p>

<p>As a reminder, any shorter prefix of a string is <strong>lexicographically smaller</strong>.</p>

<ul>
	<li>For example, <code>&quot;ab&quot;</code> is lexicographically smaller than <code>&quot;aba&quot;</code>.</li>
</ul>

<p>A leaf of a node is a node that has no children.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/30/tree1.png" style="width: 534px; height: 358px;" />
<pre>
<strong>Input:</strong> root = [0,1,2,3,4,3,4]
<strong>Output:</strong> &quot;dba&quot;
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/30/tree2.png" style="width: 534px; height: 358px;" />
<pre>
<strong>Input:</strong> root = [25,1,3,1,3,0,2]
<strong>Output:</strong> &quot;adz&quot;
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/02/01/tree3.png" style="height: 490px; width: 468px;" />
<pre>
<strong>Input:</strong> root = [2,2,1,null,1,0,null,0]
<strong>Output:</strong> &quot;abc&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 8500]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 25</code></li>
</ul>
 instead-->
<p>给定一颗根结点为&nbsp;<code>root</code>&nbsp;的二叉树，树中的每一个结点都有一个从&nbsp;<code>0</code> 到&nbsp;<code>25</code>&nbsp;的值，分别代表字母&nbsp;<code>&#39;a&#39;</code> 到&nbsp;<code>&#39;z&#39;</code>：值&nbsp;<code>0</code> 代表&nbsp;<code>&#39;a&#39;</code>，值&nbsp;<code>1</code>&nbsp;代表&nbsp;<code>&#39;b&#39;</code>，依此类推。</p>

<p>找出按字典序最小的字符串，该字符串从这棵树的一个叶结点开始，到根结点结束。</p>

<p><em>（小贴士：字符串中任何较短的前缀在字典序上都是较小的：例如，在字典序上&nbsp;<code>&quot;ab&quot;</code> 比&nbsp;<code>&quot;aba&quot;</code>&nbsp;要小。叶结点是指没有子结点的结点。）</em></p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/02/tree1.png" style="height: 107px; width: 160px;"></strong></p>

<pre><strong>输入：</strong>[0,1,2,3,4,3,4]
<strong>输出：</strong>&quot;dba&quot;
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/02/tree2.png" style="height: 107px; width: 160px;"></strong></p>

<pre><strong>输入：</strong>[25,1,3,1,3,0,2]
<strong>输出：</strong>&quot;adz&quot;
</pre>

<p><strong>示例 3：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/02/tree3.png" style="height: 180px; width: 172px;"></strong></p>

<pre><strong>输入：</strong>[2,2,1,null,1,0,null,0]
<strong>输出：</strong>&quot;abc&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>给定树的结点数介于&nbsp;<code>1</code> 和&nbsp;<code>8500</code>&nbsp;之间。</li>
	<li>树中的每个结点都有一个介于&nbsp;<code>0</code>&nbsp;和&nbsp;<code>25</code>&nbsp;之间的值。</li>
</ol>


## Note

解题思路

用变量ans存储当前最小的字符串

深度优先搜索得到从根到叶节点的字符串，翻转得到从叶节点到根的字符串，与当前最小字符串比较

若小于当前字符串就更新ans。直到遍历完所有的字符串，即可得到结果






## Solution

Language: **cpp**  /  Runtime: 12 ms

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    string ans = "z";
    void reverse(string& s){
        int len = s.size()-1;
        int mid = len/2;
        int i = 0;
        while(i<=mid){
            char temp = s[i];
            s[i] = s[len-i];
            s[len-i] = temp;
            i++;
        }
    }

    void dfs(TreeNode* root, string s){
        s += char('a' + root->val);
        if(root->left == NULL && root->right == NULL){
            reverse(s);
            if(s < ans) ans = s;
        }
        if(root->left) dfs(root->left, s);
        if(root->right) dfs(root->right, s);
    }

    string smallestFromLeaf(TreeNode* root) {
        if(root==NULL) return ans;
        dfs(root, "");
        return ans;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/smallest-string-starting-from-leaf/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/smallest-string-starting-from-leaf/description/)

Solution: [LeetCode](https://leetcode.com/articles/smallest-string-starting-from-leaf/)  /  [LeetCode中国](https://leetcode-cn.com/articles/smallest-string-starting-from-leaf/)

[回到目录](../README.md)