﻿# 889. construct-binary-tree-from-preorder-and-postorder-traversal | 根据前序和后序遍历构造二叉树

## Question description

<!--If you want to use the English description, use <p>Return any binary tree that matches the given preorder and postorder traversals.</p>

<p>Values in the traversals&nbsp;<code>pre</code> and <code>post</code>&nbsp;are distinct&nbsp;positive integers.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>pre = <span id="example-input-1-1">[1,2,4,5,3,6,7]</span>, post = <span id="example-input-1-2">[4,5,2,6,7,3,1]</span>
<strong>Output: </strong><span id="example-output-1">[1,2,3,4,5,6,7]</span>
</pre>

<p>&nbsp;</p>

<p><strong><span>Note:</span></strong></p>

<ul>
	<li><code>1 &lt;= pre.length == post.length &lt;= 30</code></li>
	<li><code>pre[]</code> and <code>post[]</code>&nbsp;are both permutations of <code>1, 2, ..., pre.length</code>.</li>
	<li>It is guaranteed an answer exists. If there exists multiple answers, you can return any of them.</li>
</ul>
</div>
 instead-->
<p>返回与给定的前序和后序遍历匹配的任何二叉树。</p>

<p>&nbsp;<code>pre</code>&nbsp;和&nbsp;<code>post</code>&nbsp;遍历中的值是不同的正整数。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>pre = [1,2,4,5,3,6,7], post = [4,5,2,6,7,3,1]
<strong>输出：</strong>[1,2,3,4,5,6,7]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= pre.length == post.length &lt;= 30</code></li>
	<li><code>pre[]</code>&nbsp;和&nbsp;<code>post[]</code>&nbsp;都是&nbsp;<code>1, 2, ..., pre.length</code>&nbsp;的排列</li>
	<li>每个输入保证至少有一个答案。如果有多个答案，可以返回其中一个。</li>
</ul>


## Note

给前序和后序求所有匹配的二叉树


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
    int[] pre, post;
    public TreeNode constructFromPrePost(int[] pre, int[] post) {
        this.pre = pre;
        this.post = post;
        return make(0, 0, pre.length);
    }

    public TreeNode make(int i0, int i1, int N) {
        if (N == 0) return null;
        TreeNode root = new TreeNode(pre[i0]);
        if (N == 1) return root;

        int L = 1;
        for (; L < N; ++L)
            if (post[i1 + L-1] == pre[i0 + 1])
                break;

        root.left = make(i0+1, i1, L);
        root.right = make(i0+L+1, i1+L, N-1-L);
        return root;
    }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/construct-binary-tree-from-preorder-and-postorder-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/construct-binary-tree-from-preorder-and-postorder-traversal/)

[回到目录](../README.md)