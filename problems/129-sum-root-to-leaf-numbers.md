# 129. sum-root-to-leaf-numbers | 求根到叶子节点数字之和

## Question description

<!--If you want to use the English description, use <p>Given a binary tree containing digits from <code>0-9</code> only, each root-to-leaf path could represent a number.</p>

<p>An example is the root-to-leaf path <code>1-&gt;2-&gt;3</code> which represents the number <code>123</code>.</p>

<p>Find the total sum of all root-to-leaf numbers.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,2,3]
    1
   / \
  2   3
<strong>Output:</strong> 25
<strong>Explanation:</strong>
The root-to-leaf path <code>1-&gt;2</code> represents the number <code>12</code>.
The root-to-leaf path <code>1-&gt;3</code> represents the number <code>13</code>.
Therefore, sum = 12 + 13 = <code>25</code>.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [4,9,0,5,1]
    4
   / \
  9   0
&nbsp;/ \
5   1
<strong>Output:</strong> 1026
<strong>Explanation:</strong>
The root-to-leaf path <code>4-&gt;9-&gt;5</code> represents the number 495.
The root-to-leaf path <code>4-&gt;9-&gt;1</code> represents the number 491.
The root-to-leaf path <code>4-&gt;0</code> represents the number 40.
Therefore, sum = 495 + 491 + 40 = <code>1026</code>.</pre>
 instead-->
<p>给定一个二叉树，它的每个结点都存放一个&nbsp;<code>0-9</code>&nbsp;的数字，每条从根到叶子节点的路径都代表一个数字。</p>

<p>例如，从根到叶子节点路径 <code>1-&gt;2-&gt;3</code> 代表数字 <code>123</code>。</p>

<p>计算从根到叶子节点生成的所有数字之和。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
    1
   / \
  2   3
<strong>输出:</strong> 25
<strong>解释:</strong>
从根到叶子节点路径 <code>1-&gt;2</code> 代表数字 <code>12</code>.
从根到叶子节点路径 <code>1-&gt;3</code> 代表数字 <code>13</code>.
因此，数字总和 = 12 + 13 = <code>25</code>.</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [4,9,0,5,1]
    4
   / \
  9   0
&nbsp;/ \
5   1
<strong>输出:</strong> 1026
<strong>解释:</strong>
从根到叶子节点路径 <code>4-&gt;9-&gt;5</code> 代表数字 495.
从根到叶子节点路径 <code>4-&gt;9-&gt;1</code> 代表数字 491.
从根到叶子节点路径 <code>4-&gt;0</code> 代表数字 40.
因此，数字总和 = 495 + 491 + 40 = <code>1026</code>.</pre>


## Note

广度优先搜索  两个队列 一个纪录节点 一个纪录当前值  用一个全局sum 

到叶节点sum+=叶节点值  最终返回sum



深度优先搜索



深度优先搜索是很直观的做法。从根节点开始，遍历每个节点，如果遇到叶子节点，则将叶子节点对应的数字加到数字之和。如果当前节点不是叶子节点，则计算其子节点对应的数字，然后对子节点递归遍历。






## Solution

Language: **cpp**  /  Runtime: 8 ms

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
    int dfs(TreeNode* root, int prevSum) {
        if (root == nullptr) {
            return 0;
        }
        int sum = prevSum * 10 + root->val;
        if (root->left == nullptr && root->right == nullptr) {
            return sum;
        } else {
            return dfs(root->left, sum) + dfs(root->right, sum);
        }
    }
    int sumNumbers(TreeNode* root) {
        return dfs(root, 0);
    }
};


```

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
    public int sumNumbers(TreeNode root) {
        if (root == null) {
            return 0;
        }
        int sum = 0;
        Queue<TreeNode> nodeQueue = new LinkedList<TreeNode>();
        Queue<Integer> numQueue = new LinkedList<Integer>();
        nodeQueue.offer(root);
        numQueue.offer(root.val);
        while (!nodeQueue.isEmpty()) {
            TreeNode node = nodeQueue.poll();
            int num = numQueue.poll();
            TreeNode left = node.left, right = node.right;
            if (left == null && right == null) {
                sum += num;
            } else {
                if (left != null) {
                    nodeQueue.offer(left);
                    numQueue.offer(num * 10 + left.val);
                }
                if (right != null) {
                    nodeQueue.offer(right);
                    numQueue.offer(num * 10 + right.val);
                }
            }
        }
        return sum;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-root-to-leaf-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-root-to-leaf-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-root-to-leaf-numbers/)

[回到目录](../README.md)