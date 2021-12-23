# LCP 34. er-cha-shu-ran-se-UGC | 二叉树染色

## Question description

<!--If you want to use the English description, use  instead-->
小扣有一个根结点为 `root` 的二叉树模型，初始所有结点均为白色，可以用蓝色染料给模型结点染色，模型的每个结点有一个 `val` 价值。小扣出于美观考虑，希望最后二叉树上每个蓝色相连部分的结点个数不能超过 `k` 个，求所有染成蓝色的结点价值总和最大是多少？


**示例 1：**
> 输入：`root = [5,2,3,4], k = 2`
>
> 输出：`12`
>
> 解释：`结点 5、3、4 染成蓝色，获得最大的价值 5+3+4=12`
![image.png](https://pic.leetcode-cn.com/1616126267-BqaCRj-image.png)


**示例 2：**
> 输入：`root = [4,1,3,9,null,null,2], k = 2`
>
> 输出：`16`
>
> 解释：结点 4、3、9 染成蓝色，获得最大的价值 4+3+9=16
![image.png](https://pic.leetcode-cn.com/1616126301-gJbhba-image.png)



**提示：**
+ `1 <= k <= 10`
+ `1 <= val <= 10000`
+ `1 <= 结点数量 <= 10000`
    



## Solution

Language: **java**  /  Runtime: 9 ms

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
  public int maxValue(TreeNode root, int k) {
    int[] dp = dynamic(root, k);
    int max = Integer.MIN_VALUE;
    for (int i = 0; i <= k; i++) {
      //取root的各种染色情况的最大值
      max = Math.max(max, dp[i]);
    }
    return max;
  }

  private int[] dynamic(TreeNode root, int k) {
    int[] dp = new int[k + 1];
    //1.初始化：空节点为底，自底向上
    if (root == null) return dp;
    //2.获取左、右子树染色状态的dp表
    //- 左子树
    int[] l = dynamic(root.left, k);
    //- 右子树
    int[] r = dynamic(root.right, k);
    //3.更新处理root 染色/不染色 的情况下的dp表
    //- 不染root
    int ml = Integer.MIN_VALUE, mr = Integer.MIN_VALUE;
    for (int i = 0; i <= k; i++) {
      //- 分别取子节点的最大值
      ml = Math.max(ml, l[i]);
      mr = Math.max(mr, r[i]);
    }
    dp[0] = ml + mr;
    //- 染root
    for (int i = 1; i <= k; i++) {
      for (int j = 0; j < i; j++) {
        //- 还需要染色 i - 1 个点，左子树 j 个，右子树 i-1-j 个
        dp[i] = Math.max(dp[i], root.val + l[j] + r[i - 1 - j]);
      }
    }
    //4.更新完毕，返回后继续向上动态规划
    return dp;
  }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/er-cha-shu-ran-se-UGC/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/er-cha-shu-ran-se-UGC/description/)

Solution: [LeetCode](https://leetcode.com/articles/er-cha-shu-ran-se-UGC/)  /  [LeetCode中国](https://leetcode-cn.com/articles/er-cha-shu-ran-se-UGC/)

[回到目录](../README.md)