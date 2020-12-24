# 105. construct-binary-tree-from-preorder-and-inorder-traversal | 从前序与中序遍历序列构造二叉树

## Question description

<!--If you want to use the English description, use <p>Given preorder and inorder traversal of a tree, construct the binary tree.</p>

<p><strong>Note:</strong><br />
You may assume that duplicates do not exist in the tree.</p>

<p>For example, given</p>

<pre>
preorder =&nbsp;[3,9,20,15,7]
inorder = [9,3,15,20,7]</pre>

<p>Return the following binary tree:</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7</pre>
 instead-->
<p>根据一棵树的前序遍历与中序遍历构造二叉树。</p>

<p><strong>注意:</strong><br>
你可以假设树中没有重复的元素。</p>

<p>例如，给出</p>

<pre>前序遍历 preorder =&nbsp;[3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]</pre>

<p>返回如下的二叉树：</p>

<pre>    3
   / \
  9  20
    /  \
   15   7</pre>




## Solution

Language: **java**  /  Runtime: 7 ms

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
  // start from first preorder element
  int pre_idx = 0;
  int[] preorder;
  int[] inorder;
  HashMap<Integer, Integer> idx_map = new HashMap<Integer, Integer>();

  public TreeNode helper(int in_left, int in_right) {
    // if there is no elements to construct subtrees
    if (in_left == in_right)
      return null;

    // pick up pre_idx element as a root
    int root_val = preorder[pre_idx];
    TreeNode root = new TreeNode(root_val);

    // root splits inorder list
    // into left and right subtrees
    int index = idx_map.get(root_val);

    // recursion 
    pre_idx++;
    // build left subtree
    root.left = helper(in_left, index);
    // build right subtree
    root.right = helper(index + 1, in_right);
    return root;
  }

  public TreeNode buildTree(int[] preorder, int[] inorder) {
    this.preorder = preorder;
    this.inorder = inorder;

    // build a hashmap value -> its index
    int idx = 0;
    for (Integer val : inorder)
      idx_map.put(val, idx++);
    return helper(0, inorder.length);
  }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/construct-binary-tree-from-preorder-and-inorder-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/construct-binary-tree-from-preorder-and-inorder-traversal/)

[回到目录](../README.md)