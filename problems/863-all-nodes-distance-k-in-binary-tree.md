# 863. all-nodes-distance-k-in-binary-tree | 二叉树中所有距离为 K 的结点

## Question description

<!--If you want to use the English description, use <p>Given the <code>root</code> of a binary tree, the value of a target node <code>target</code>, and an integer <code>k</code>, return <em>an array of the values of all nodes that have a distance </em><code>k</code><em> from the target node.</em></p>

<p>You can return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/06/28/sketch0.png" style="width: 500px; height: 429px;" />
<pre>
<strong>Input:</strong> root = [3,5,1,6,2,0,8,null,null,7,4], target = 5, k = 2
<strong>Output:</strong> [7,4,1]
Explanation: The nodes that are a distance 2 from the target node (with value 5) have values 7, 4, and 1.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [1], target = 1, k = 3
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 500]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 500</code></li>
	<li>All the values <code>Node.val</code> are <strong>unique</strong>.</li>
	<li><code>target</code> is the value of one of the nodes in the tree.</li>
	<li><code>0 &lt;= k &lt;= 1000</code></li>
</ul>
 instead-->
<p>给定一个二叉树（具有根结点&nbsp;<code>root</code>），&nbsp;一个目标结点&nbsp;<code>target</code>&nbsp;，和一个整数值 <code>K</code> 。</p>

<p>返回到目标结点 <code>target</code> 距离为 <code>K</code> 的所有结点的值的列表。 答案可以以任何顺序返回。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>root = [3,5,1,6,2,0,8,null,null,7,4], target = 5, K = 2
<strong>输出：</strong>[7,4,1]
<strong>解释：</strong>
所求结点为与目标结点（值为 5）距离为 2 的结点，
值分别为 7，4，以及 1

<img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/06/28/sketch0.png" style="height: 240px; width: 280px;">

注意，输入的 &quot;root&quot; 和 &quot;target&quot; 实际上是树上的结点。
上面的输入仅仅是对这些对象进行了序列化描述。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>给定的树是非空的。</li>
	<li>树上的每个结点都具有唯一的值&nbsp;<code>0 &lt;= node.val &lt;= 500</code>&nbsp;。</li>
	<li>目标结点&nbsp;<code>target</code>&nbsp;是树上的结点。</li>
	<li><code>0 &lt;= K &lt;= 1000</code>.</li>
</ol>


## Note

C++  DFS   BFS



解题思路

首先使用 DFS 遍历二叉树，为每个节点保存其父结点；

使用 BFS 向三个方向搜索（左孩子、右孩子、父结点），当搜索第 K 次时，队列中的全部结点即为所求；



注意：



BFS 要保存已访问结点；

每次都将当前队列中全部元素向外延伸一个结点；






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
private:
  unordered_map<TreeNode *, TreeNode *> parent;

public:
  vector<int> distanceK(TreeNode *root, TreeNode *target, int K) {
    dfs(root, NULL); //记录父结点
    queue<TreeNode *> Q;
    unordered_set<TreeNode *> visited;
    Q.push(target); // target结点入队，从 target 结点开始向外延伸
    visited.insert(target);
    while (!Q.empty()) {
      if (K-- == 0) { // 延伸 K 次，队中全部结点即为所求
        vector<int> ret;
        while (!Q.empty()) {
          ret.push_back(Q.front()->val);
          Q.pop();
        }
        return ret;
      } else {
        int n = Q.size(); // 将当前队中所有结点向外延伸 1 个结点
        for (int i = 0; i < n; i++) {
          TreeNode *node = Q.front();
          Q.pop();
          if (node->left && visited.find(node->left) == visited.end()) {
            Q.push(node->left);
            visited.insert(node->left);
          }
          if (node->right && visited.find(node->right) == visited.end()) {
            Q.push(node->right);
            visited.insert(node->right);
          }
          if (parent[node] != NULL &&
              visited.find(parent[node]) == visited.end()) {
            Q.push(parent[node]);
            visited.insert(parent[node]);
          }
        }
      }
    }
    return vector<int>();
  }
  void dfs(TreeNode *root, TreeNode *pre) {
    if (root) {
      parent.insert({root, pre});
      dfs(root->left, root);
      dfs(root->right, root);
    }
  }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/all-nodes-distance-k-in-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/all-nodes-distance-k-in-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/all-nodes-distance-k-in-binary-tree/)

[回到目录](../README.md)