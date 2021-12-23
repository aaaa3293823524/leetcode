# 2073. time-needed-to-buy-tickets | 买票需要的时间

## Question description

<!--If you want to use the English description, use <p>There are <code>n</code> people in a line queuing to buy tickets, where the <code>0<sup>th</sup></code> person is at the <strong>front</strong> of the line and the <code>(n - 1)<sup>th</sup></code> person is at the <strong>back</strong> of the line.</p>

<p>You are given a <strong>0-indexed</strong> integer array <code>tickets</code> of length <code>n</code> where the number of tickets that the <code>i<sup>th</sup></code> person would like to buy is <code>tickets[i]</code>.</p>

<p>Each person takes <strong>exactly 1 second</strong> to buy a ticket. A person can only buy <strong>1 ticket at a time</strong> and has to go back to <strong>the end</strong> of the line (which happens <strong>instantaneously</strong>) in order to buy more tickets. If a person does not have any tickets left to buy, the person will <strong>leave </strong>the line.</p>

<p>Return <em>the <strong>time taken</strong> for the person at position </em><code>k</code><em>&nbsp;</em><strong><em>(0-indexed)</em>&nbsp;</strong><em>to finish buying tickets</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> tickets = [2,3,2], k = 2
<strong>Output:</strong> 6
<strong>Explanation:</strong> 
- In the first pass, everyone in the line buys a ticket and the line becomes [1, 2, 1].
- In the second pass, everyone in the line buys a ticket and the line becomes [0, 1, 0].
The person at&nbsp;position 2 has successfully bought 2 tickets and it took 3 + 3 = 6 seconds.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> tickets = [5,1,1,1], k = 0
<strong>Output:</strong> 8
<strong>Explanation:</strong>
- In the first pass, everyone in the line buys a ticket and the line becomes [4, 0, 0, 0].
- In the next 4 passes, only the person in position 0 is buying tickets.
The person at&nbsp;position 0 has successfully bought 5 tickets and it took 4 + 1 + 1 + 1 + 1 = 8 seconds.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == tickets.length</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>1 &lt;= tickets[i] &lt;= 100</code></li>
	<li><code>0 &lt;= k &lt; n</code></li>
</ul>
 instead-->
<p>有 <code>n</code> 个人前来排队买票，其中第 <code>0</code> 人站在队伍 <strong>最前方</strong> ，第 <code>(n - 1)</code> 人站在队伍 <strong>最后方</strong> 。</p>

<p>给你一个下标从 <strong>0</strong> 开始的整数数组 <code>tickets</code> ，数组长度为 <code>n</code> ，其中第 <code>i</code> 人想要购买的票数为 <code>tickets[i]</code> 。</p>

<p>每个人买票都需要用掉 <strong>恰好 1 秒</strong> 。一个人 <strong>一次只能买一张票</strong> ，如果需要购买更多票，他必须走到&nbsp; <strong>队尾</strong> 重新排队（<strong>瞬间 </strong>发生，不计时间）。如果一个人没有剩下需要买的票，那他将会 <strong>离开</strong> 队伍。</p>

<p>返回位于位置 <code>k</code>（下标从 <strong>0</strong> 开始）的人完成买票需要的时间（以秒为单位）。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>tickets = [2,3,2], k = 2
<strong>输出：</strong>6
<strong>解释：</strong> 
- 第一轮，队伍中的每个人都买到一张票，队伍变为 [1, 2, 1] 。
- 第二轮，队伍中的每个都又都买到一张票，队伍变为 [0, 1, 0] 。
位置 2 的人成功买到 2 张票，用掉 3 + 3 = 6 秒。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>tickets = [5,1,1,1], k = 0
<strong>输出：</strong>8
<strong>解释：</strong>
- 第一轮，队伍中的每个人都买到一张票，队伍变为 [4, 0, 0, 0] 。
- 接下来的 4 轮，只有位置 0 的人在买票。
位置 0 的人成功买到 5 张票，用掉 4 + 1 + 1 + 1 + 1 = 8 秒。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == tickets.length</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>1 &lt;= tickets[i] &lt;= 100</code></li>
	<li><code>0 &lt;= k &lt; n</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public static int timeRequiredToBuy(int[] tickets, int k) {
        int n=tickets.length;
        int sum=0;
        int count=0;
        int t=tickets[k];
        while(count<t) {
            for(int i=0;i<n;i++) {
                if(tickets[i]>0) {
                    tickets[i]--;
                    sum++;
                }
                if(count==(t-1)&&i==k)break;
            }
            count++;
        }

        return sum;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/time-needed-to-buy-tickets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/time-needed-to-buy-tickets/description/)

Solution: [LeetCode](https://leetcode.com/articles/time-needed-to-buy-tickets/)  /  [LeetCode中国](https://leetcode-cn.com/articles/time-needed-to-buy-tickets/)

[回到目录](../README.md)