# 剑指 Offer 32 - III. cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof | 从上到下打印二叉树 III

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。</p>

<p>&nbsp;</p>

<p>例如:<br>
给定二叉树:&nbsp;<code>[3,9,20,null,null,15,7]</code>,</p>

<pre>    3
   / \
  9  20
    /  \
   15   7
</pre>

<p>返回其层次遍历结果：</p>

<pre>[
  [3],
  [20,9],
  [15,7]
]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>节点总数 &lt;= 1000</code></li>
</ol>


## Note

双端队列


## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        List<List<Integer>> res = new ArrayList<>();
        if(root != null) queue.add(root);
        while(!queue.isEmpty()) {
            LinkedList<Integer> tmp = new LinkedList<>();
            for(int i = queue.size(); i > 0; i--) {
                TreeNode node = queue.poll();
                if(res.size() % 2 == 0) tmp.addLast(node.val); // 偶数层 -> 队列头部
                else tmp.addFirst(node.val); // 奇数层 -> 队列尾部
                if(node.left != null) queue.add(node.left);
                if(node.right != null) queue.add(node.right);
            }
            res.add(tmp);
        }
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

[回到目录](../README.md)