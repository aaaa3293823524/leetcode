# 1626. best-team-with-no-conflicts | 无矛盾的最佳球队

## Question description

<!--If you want to use the English description, use <p>You are the manager of a basketball team. For the upcoming tournament, you want to choose the team with the highest overall score. The score of the team is the <strong>sum</strong> of scores of all the players in the team.</p>

<p>However, the basketball team is not allowed to have <strong>conflicts</strong>. A <strong>conflict</strong> exists if a younger player has a <strong>strictly higher</strong> score than an older player. A conflict does <strong>not</strong> occur between players of the same age.</p>

<p>Given two lists, <code>scores</code> and <code>ages</code>, where each <code>scores[i]</code> and <code>ages[i]</code> represents the score and age of the <code>i<sup>th</sup></code> player, respectively, return <em>the highest overall score of all possible basketball teams</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> scores = [1,3,5,10,15], ages = [1,2,3,4,5]
<strong>Output:</strong> 34
<strong>Explanation:</strong>&nbsp;You can choose all the players.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> scores = [4,5,6,5], ages = [2,1,2,1]
<strong>Output:</strong> 16
<strong>Explanation:</strong>&nbsp;It is best to choose the last 3 players. Notice that you are allowed to choose multiple people of the same age.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> scores = [1,2,3,5], ages = [8,9,10,1]
<strong>Output:</strong> 6
<strong>Explanation:</strong>&nbsp;It is best to choose the first 3 players. 
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= scores.length, ages.length &lt;= 1000</code></li>
	<li><code>scores.length == ages.length</code></li>
	<li><code>1 &lt;= scores[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>1 &lt;= ages[i] &lt;= 1000</code></li>
</ul>
 instead-->
<p>假设你是球队的经理。对于即将到来的锦标赛，你想组合一支总体得分最高的球队。球队的得分是球队中所有球员的分数 <strong>总和</strong> 。</p>

<p>然而，球队中的矛盾会限制球员的发挥，所以必须选出一支 <strong>没有矛盾</strong> 的球队。如果一名年龄较小球员的分数 <strong>严格大于</strong> 一名年龄较大的球员，则存在矛盾。同龄球员之间不会发生矛盾。</p>

<p>给你两个列表 <code>scores</code> 和 <code>ages</code>，其中每组 <code>scores[i]</code> 和 <code>ages[i]</code> 表示第 <code>i</code> 名球员的分数和年龄。请你返回 <strong>所有可能的无矛盾球队中得分最高那支的分数</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>scores = [1,3,5,10,15], ages = [1,2,3,4,5]
<strong>输出：</strong>34
<strong>解释：</strong>你可以选中所有球员。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>scores = [4,5,6,5], ages = [2,1,2,1]
<strong>输出：</strong>16
<strong>解释：</strong>最佳的选择是后 3 名球员。注意，你可以选中多个同龄球员。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>scores = [1,2,3,5], ages = [8,9,10,1]
<strong>输出：</strong>6
<strong>解释：</strong>最佳的选择是前 3 名球员。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= scores.length, ages.length &lt;= 1000</code></li>
	<li><code>scores.length == ages.length</code></li>
	<li><code>1 &lt;= scores[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>1 &lt;= ages[i] &lt;= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 48 ms

```java
class Solution {
    public int bestTeamScore(int[] scores, int[] ages) {
        if(scores.length == 1)
            return scores[0];
            
        int[][] arr = new int[scores.length][2];
        for(int i = 0; i < scores.length; i++){
            arr[i][0] = ages[i];
            arr[i][1] = scores[i];
        }
        Arrays.sort(arr, new Comparator<int[]>() {
            public int compare(int[] o1, int[] o2) {
                if(o1[0]==o2[0])
                    return o1[1]-o2[1];
                return o1[0]-o2[0];
            }
        });

        int[] dp = new int[scores.length];
        for(int i = 0; i < scores.length; i++){
            dp[i] = arr[i][1];
        }

        int ans = 0;
        for(int i = 0; i < scores.length; i++) {
            for(int j = 0; j < i; j++) { // 找在i之前有没有比i小的
                if(arr[j][1] <= arr[i][1]) {
                    dp[i] = Math.max(dp[j]+arr[i][1], dp[i]);
                }
                ans = Math.max(ans,dp[i]);
            }
        }

        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/best-team-with-no-conflicts/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-team-with-no-conflicts/description/)

Solution: [LeetCode](https://leetcode.com/articles/best-team-with-no-conflicts/)  /  [LeetCode中国](https://leetcode-cn.com/articles/best-team-with-no-conflicts/)

[回到目录](../README.md)