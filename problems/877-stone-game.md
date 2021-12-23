﻿# 877. stone-game | 石子游戏

## Question description

<!--If you want to use the English description, use <p>Alice and Bob play a game with piles of stones. There are an <strong>even</strong> number of piles arranged in a row, and each pile has a <strong>positive</strong> integer number of stones <code>piles[i]</code>.</p>

<p>The objective of the game is to end with the most stones. The <strong>total</strong> number of stones across all the piles is <strong>odd</strong>, so there are no ties.</p>

<p>Alice and Bob take turns, with <strong>Alice starting first</strong>. Each turn, a player takes the entire pile of stones either from the <strong>beginning</strong> or from the <strong>end</strong> of the row. This continues until there are no more piles left, at which point the person with the <strong>most stones wins</strong>.</p>

<p>Assuming Alice and Bob play optimally, return <code>true</code><em> if Alice wins the game, or </em><code>false</code><em> if Bob wins</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> piles = [5,3,4,5]
<strong>Output:</strong> true
<strong>Explanation:</strong> 
Alice starts first, and can only take the first 5 or the last 5.
Say she takes the first 5, so that the row becomes [3, 4, 5].
If Bob takes 3, then the board is [4, 5], and Alice takes 5 to win with 10 points.
If Bob takes the last 5, then the board is [3, 4], and Alice takes 4 to win with 9 points.
This demonstrated that taking the first 5 was a winning move for Alice, so we return true.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> piles = [3,7,2,3]
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= piles.length &lt;= 500</code></li>
	<li><code>piles.length</code> is <strong>even</strong>.</li>
	<li><code>1 &lt;= piles[i] &lt;= 500</code></li>
	<li><code>sum(piles[i])</code> is <strong>odd</strong>.</li>
</ul>
 instead-->
<p>Alice 和 Bob 用几堆石子在做游戏。一共有偶数堆石子，<strong>排成一行</strong>；每堆都有 <strong>正</strong> 整数颗石子，数目为 <code>piles[i]</code>&nbsp;。</p>

<p>游戏以谁手中的石子最多来决出胜负。石子的 <strong>总数</strong> 是 <strong>奇数</strong> ，所以没有平局。</p>

<p>Alice 和 Bob 轮流进行，<strong>Alice 先开始</strong> 。 每回合，玩家从行的 <strong>开始</strong> 或 <strong>结束</strong> 处取走整堆石头。 这种情况一直持续到没有更多的石子堆为止，此时手中 <strong>石子最多</strong> 的玩家 <strong>获胜</strong> 。</p>

<p>假设 Alice 和 Bob 都发挥出最佳水平，当 Alice 赢得比赛时返回&nbsp;<code>true</code>&nbsp;，当 Bob 赢得比赛时返回&nbsp;<code>false</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>piles = [5,3,4,5]
<strong>输出：</strong>true
<strong>解释：</strong>
Alice 先开始，只能拿前 5 颗或后 5 颗石子 。
假设他取了前 5 颗，这一行就变成了 [3,4,5] 。
如果 Bob 拿走前 3 颗，那么剩下的是 [4,5]，Alice 拿走后 5 颗赢得 10 分。
如果 Bob 拿走后 5 颗，那么剩下的是 [3,4]，Alice 拿走后 4 颗赢得 9 分。
这表明，取前 5 颗石子对 Alice 来说是一个胜利的举动，所以返回 true 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>piles = [3,7,2,3]
<strong>输出：</strong>true
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= piles.length &lt;= 500</code></li>
	<li><code>piles.length</code> 是 <strong>偶数</strong></li>
	<li><code>1 &lt;= piles[i] &lt;= 500</code></li>
	<li><code>sum(piles[i])</code>&nbsp;是 <strong>奇数</strong></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def stoneGame(self, piles: List[int]) -> bool:
        return True
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/stone-game/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/stone-game/description/)

Solution: [LeetCode](https://leetcode.com/articles/stone-game/)  /  [LeetCode中国](https://leetcode-cn.com/articles/stone-game/)

[回到目录](../README.md)