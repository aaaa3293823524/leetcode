# 剑指 Offer 28. dui-cheng-de-er-cha-shu-lcof | 对称的二叉树

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。</p>

<p>例如，二叉树&nbsp;[1,2,2,3,4,4,3] 是对称的。</p>

<p><code>&nbsp; &nbsp; 1<br>
&nbsp; &nbsp;/ \<br>
&nbsp; 2 &nbsp; 2<br>
&nbsp;/ \ / \<br>
3 &nbsp;4 4 &nbsp;3</code><br>
但是下面这个&nbsp;[1,2,2,null,3,null,3] 则不是镜像对称的:</p>

<p><code>&nbsp; &nbsp; 1<br>
&nbsp; &nbsp;/ \<br>
&nbsp; 2 &nbsp; 2<br>
&nbsp; &nbsp;\ &nbsp; \<br>
&nbsp; &nbsp;3 &nbsp; &nbsp;3</code></p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>root = [1,2,2,3,4,4,3]
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>root = [1,2,2,null,3,null,3]
<strong>输出：</strong>false</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= 节点个数 &lt;= 1000</code></p>

<p>注意：本题与主站 101 题相同：<a href="https://leetcode-cn.com/problems/symmetric-tree/">https://leetcode-cn.com/problems/symmetric-tree/</a></p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        return root == null ? true : recur(root.left, root.right);
    }
    boolean recur(TreeNode L, TreeNode R) {
        if(L == null && R == null) return true;
        if(L == null || R == null || L.val != R.val) return false;
        return recur(L.left, R.right) && recur(L.right, R.left);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/dui-cheng-de-er-cha-shu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/dui-cheng-de-er-cha-shu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/dui-cheng-de-er-cha-shu-lcof/)

[回到目录](../README.md)