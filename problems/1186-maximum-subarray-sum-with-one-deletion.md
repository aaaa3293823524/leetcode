# 1186. maximum-subarray-sum-with-one-deletion | 删除一次得到子数组最大和

## Question description

<!--If you want to use the English description, use <p>Given an array of integers, return the maximum sum for a <strong>non-empty</strong>&nbsp;subarray (contiguous elements) with at most one element deletion.&nbsp;In other words, you want to choose a subarray and optionally delete one element from it so that there is still at least one element left and the&nbsp;sum of the remaining elements is maximum possible.</p>

<p>Note that the subarray needs to be <strong>non-empty</strong> after deleting one element.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,-2,0,3]
<strong>Output:</strong> 4
<strong>Explanation: </strong>Because we can choose [1, -2, 0, 3] and drop -2, thus the subarray [1, 0, 3] becomes the maximum value.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,-2,-2,3]
<strong>Output:</strong> 3
<strong>Explanation: </strong>We just choose [3] and it&#39;s the maximum sum.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [-1,-1,-1,-1]
<strong>Output:</strong> -1
<strong>Explanation:</strong>&nbsp;The final subarray needs to be non-empty. You can&#39;t choose [-1] and delete -1 from it, then get an empty subarray to make the sum equals to 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= arr[i] &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个整数数组，返回它的某个&nbsp;<strong>非空</strong> 子数组（连续元素）在执行一次可选的删除操作后，所能得到的最大元素总和。</p>

<p>换句话说，你可以从原数组中选出一个子数组，并可以决定要不要从中删除一个元素（只能删一次哦），（删除后）子数组中至少应当有一个元素，然后该子数组（剩下）的元素总和是所有子数组之中最大的。</p>

<p>注意，删除一个元素后，子数组 <strong>不能为空</strong>。</p>

<p>请看示例：</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>arr = [1,-2,0,3]
<strong>输出：</strong>4
<strong>解释：</strong>我们可以选出 [1, -2, 0, 3]，然后删掉 -2，这样得到 [1, 0, 3]，和最大。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>arr = [1,-2,-2,3]
<strong>输出：</strong>3
<strong>解释：</strong>我们直接选出 [3]，这就是最大和。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>arr = [-1,-1,-1,-1]
<strong>输出：</strong>-1
<strong>解释：</strong>最后得到的子数组不能为空，所以我们不能选择 [-1] 并从中删去 -1 来得到 0。
     我们应该直接选择 [-1]，或者选择 [-1, -1] 再从中删去一个 -1。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10^5</code></li>
	<li><code>-10^4 &lt;= arr[i] &lt;= 10^4</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
class Solution {
    public int maximumSum(int[] arr) {
        /**
            要定义两个动态规划数组
            我们定义数组dp1和dp2，其中dp1数组表示不删除元素的情况下最大子数组和，dp2代表删除元素的
            情况下的最大子数组和。
         */
        int n = arr.length;
        int[] dp1 = new int[n];
        int[] dp2 = new int[n];
        int res = arr[0];
        dp1[0] = arr[0];
        //保证dp2[1]存储的是dp1[0]
        dp2[0] = -100000;
        for(int i = 1; i < n; i++){
            dp1[i] = Math.max(dp1[i - 1] + arr[i], arr[i]);
            //dp2代表删除元素的情况下的最大子数组和
            dp2[i] = Math.max(dp2[i - 1] + arr[i], dp1[i - 1]);
            res = Math.max(res, Math.max(dp1[i], dp2[i]));
        }
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-subarray-sum-with-one-deletion/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-subarray-sum-with-one-deletion/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-subarray-sum-with-one-deletion/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-subarray-sum-with-one-deletion/)

[回到目录](../README.md)