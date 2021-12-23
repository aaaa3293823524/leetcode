# 1696. jump-game-vi | 跳跃游戏 VI

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>0-indexed</strong> integer array <code>nums</code> and an integer <code>k</code>.</p>

<p>You are initially standing at index <code>0</code>. In one move, you can jump at most <code>k</code> steps forward without going outside the boundaries of the array. That is, you can jump from index <code>i</code> to any index in the range <code>[i + 1, min(n - 1, i + k)]</code> <strong>inclusive</strong>.</p>

<p>You want to reach the last index of the array (index <code>n - 1</code>). Your <strong>score</strong> is the <strong>sum</strong> of all <code>nums[j]</code> for each index <code>j</code> you visited in the array.</p>

<p>Return <em>the <strong>maximum score</strong> you can get</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [<u>1</u>,<u>-1</u>,-2,<u>4</u>,-7,<u>3</u>], k = 2
<strong>Output:</strong> 7
<strong>Explanation:</strong> You can choose your jumps forming the subsequence [1,-1,4,3] (underlined above). The sum is 7.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [<u>10</u>,-5,-2,<u>4</u>,0,<u>3</u>], k = 3
<strong>Output:</strong> 17
<strong>Explanation:</strong> You can choose your jumps forming the subsequence [10,4,3] (underlined above). The sum is 17.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,-5,-20,4,-1,3,-6,-3], k = 2
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length, k &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个下标从 <strong>0</strong> 开始的整数数组 <code>nums</code> 和一个整数 <code>k</code> 。</p>

<p>一开始你在下标 <code>0</code> 处。每一步，你最多可以往前跳 <code>k</code> 步，但你不能跳出数组的边界。也就是说，你可以从下标 <code>i</code> 跳到 <code>[i + 1， min(n - 1, i + k)]</code> <strong>包含</strong> 两个端点的任意位置。</p>

<p>你的目标是到达数组最后一个位置（下标为 <code>n - 1</code> ），你的 <strong>得分</strong> 为经过的所有数字之和。</p>

<p>请你返回你能得到的 <strong>最大得分</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>nums = [<strong>1</strong>,<strong>-1</strong>,-2,<strong>4</strong>,-7,<strong>3</strong>], k = 2
<b>输出：</b>7
<b>解释：</b>你可以选择子序列 [1,-1,4,3] （上面加粗的数字），和为 7 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [<strong>10</strong>,-5,-2,<strong>4</strong>,0,<strong>3</strong>], k = 3
<b>输出：</b>17
<b>解释：</b>你可以选择子序列 [10,4,3] （上面加粗数字），和为 17 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>nums = [1,-5,-20,4,-1,3,-6,-3], k = 2
<b>输出：</b>0
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li> <code>1 <= nums.length, k <= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> <= nums[i] <= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 53 ms

```java
class Solution {
    public int maxResult(int[] nums, int k) {
        int len = nums.length;
        Queue<int[]> queue = new PriorityQueue<>((o1, o2) -> o2[0] - o1[0]);
        queue.offer(new int[]{nums[0], 0});
        int res = nums[0];
        for (int i = 1; i < len; i++) {
            while (i - queue.peek()[1] > k){
                queue.poll();
            }
            res = queue.peek()[0] + nums[i];
            queue.offer(new int[]{res, i});
        }
        return res;
    }
//   public int maxResult(int[] nums, int k) {
//     if (nums.length == 1) {
//       return nums[0];
//     }
//     int length = nums.length;
//     // dp[i] = 到达i位置可得的最大分数
//     int[] dp = new int[length];
//     // 初始化除0外的所有值为最小
//     dp[0] = nums[0];
//     for (int i = 1; i < length; i++) {
//       dp[i] = Integer.MIN_VALUE;
//     }
//     for (int i = 0; i < length; i++) {
//       // dp[i]可到达的所有位置
//       for (int j = i+1; j < length && j <= i+k; j++) {
//         // 从i跳跃到j位置, j位置的最大得分
//         int nextNum = dp[i]+nums[j];
//         // 如果比j位置当前最大得分大, 则更新j位置最大得分
//         if (dp[j] < nextNum) {
//           dp[j] = nextNum;
//         }
//         // 剪枝, i后面能影响到的分数, 可以由遍历到j时进行更新
//         if (dp[j] >= dp[i]) {
//           break;
//         }
//       }
//     }
//     return dp[length-1];
//   }
}



```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/jump-game-vi/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/jump-game-vi/description/)

Solution: [LeetCode](https://leetcode.com/articles/jump-game-vi/)  /  [LeetCode中国](https://leetcode-cn.com/articles/jump-game-vi/)

[回到目录](../README.md)