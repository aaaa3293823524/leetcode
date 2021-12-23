# 1942. the-number-of-the-smallest-unoccupied-chair | 最小未被占据椅子的编号

## Question description

<!--If you want to use the English description, use <p>There is a party where <code>n</code> friends numbered from <code>0</code> to <code>n - 1</code> are attending. There is an <strong>infinite</strong> number of chairs in this party that are numbered from <code>0</code> to <code>infinity</code>. When a friend arrives at the party, they sit on the unoccupied chair with the <strong>smallest number</strong>.</p>

<ul>
	<li>For example, if chairs <code>0</code>, <code>1</code>, and <code>5</code> are occupied when a friend comes, they will sit on chair number <code>2</code>.</li>
</ul>

<p>When a friend leaves the party, their chair becomes unoccupied at the moment they leave. If another friend arrives at that same moment, they can sit in that chair.</p>

<p>You are given a <strong>0-indexed</strong> 2D integer array <code>times</code> where <code>times[i] = [arrival<sub>i</sub>, leaving<sub>i</sub>]</code>, indicating the arrival and leaving times of the <code>i<sup>th</sup></code> friend respectively, and an integer <code>targetFriend</code>. All arrival times are <strong>distinct</strong>.</p>

<p>Return<em> the <strong>chair number</strong> that the friend numbered </em><code>targetFriend</code><em> will sit on</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> times = [[1,4],[2,3],[4,6]], targetFriend = 1
<strong>Output:</strong> 1
<strong>Explanation:</strong> 
- Friend 0 arrives at time 1 and sits on chair 0.
- Friend 1 arrives at time 2 and sits on chair 1.
- Friend 1 leaves at time 3 and chair 1 becomes empty.
- Friend 0 leaves at time 4 and chair 0 becomes empty.
- Friend 2 arrives at time 4 and sits on chair 0.
Since friend 1 sat on chair 1, we return 1.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> times = [[3,10],[1,5],[2,6]], targetFriend = 0
<strong>Output:</strong> 2
<strong>Explanation:</strong> 
- Friend 1 arrives at time 1 and sits on chair 0.
- Friend 2 arrives at time 2 and sits on chair 1.
- Friend 0 arrives at time 3 and sits on chair 2.
- Friend 1 leaves at time 5 and chair 0 becomes empty.
- Friend 2 leaves at time 6 and chair 1 becomes empty.
- Friend 0 leaves at time 10 and chair 2 becomes empty.
Since friend 0 sat on chair 2, we return 2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == times.length</code></li>
	<li><code>2 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>times[i].length == 2</code></li>
	<li><code>1 &lt;= arrival<sub>i</sub> &lt; leaving<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= targetFriend &lt;= n - 1</code></li>
	<li>Each <code>arrival<sub>i</sub></code> time is <strong>distinct</strong>.</li>
</ul>
 instead-->
<p>有 <code>n</code> 个朋友在举办一个派对，这些朋友从 <code>0</code> 到 <code>n - 1</code> 编号。派对里有 <strong>无数</strong> 张椅子，编号为 <code>0</code> 到 <code>infinity</code> 。当一个朋友到达派对时，他会占据 <strong>编号最小</strong> 且未被占据的椅子。</p>

<ul>
	<li>比方说，当一个朋友到达时，如果椅子 <code>0</code> ，<code>1</code> 和 <code>5</code> 被占据了，那么他会占据 <code>2</code> 号椅子。</li>
</ul>

<p>当一个朋友离开派对时，他的椅子会立刻变成未占据状态。如果同一时刻有另一个朋友到达，可以立即占据这张椅子。</p>

<p>给你一个下标从 <strong>0</strong> 开始的二维整数数组 <code>times</code> ，其中 <code>times[i] = [arrival<sub>i</sub>, leaving<sub>i</sub>]</code> 表示第 <code>i</code> 个朋友到达和离开的时刻，同时给你一个整数 <code>targetFriend</code> 。所有到达时间 <strong>互不相同</strong> 。</p>

<p>请你返回编号为 <code>targetFriend</code> 的朋友占据的 <strong>椅子编号</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>times = [[1,4],[2,3],[4,6]], targetFriend = 1
<b>输出：</b>1
<b>解释：</b>
- 朋友 0 时刻 1 到达，占据椅子 0 。
- 朋友 1 时刻 2 到达，占据椅子 1 。
- 朋友 1 时刻 3 离开，椅子 1 变成未占据。
- 朋友 0 时刻 4 离开，椅子 0 变成未占据。
- 朋友 2 时刻 4 到达，占据椅子 0 。
朋友 1 占据椅子 1 ，所以返回 1 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>times = [[3,10],[1,5],[2,6]], targetFriend = 0
<b>输出：</b>2
<b>解释：</b>
- 朋友 1 时刻 1 到达，占据椅子 0 。
- 朋友 2 时刻 2 到达，占据椅子 1 。
- 朋友 0 时刻 3 到达，占据椅子 2 。
- 朋友 1 时刻 5 离开，椅子 0 变成未占据。
- 朋友 2 时刻 6 离开，椅子 1 变成未占据。
- 朋友 0 时刻 10 离开，椅子 2 变成未占据。
朋友 0 占据椅子 2 ，所以返回 2 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == times.length</code></li>
	<li><code>2 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>times[i].length == 2</code></li>
	<li><code>1 &lt;= arrival<sub>i</sub> &lt; leaving<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= targetFriend &lt;= n - 1</code></li>
	<li>每个 <code>arrival<sub>i</sub></code> 时刻 <strong>互不相同</strong> 。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 65 ms

```java
class Solution {
    public int smallestChair(int[][] times, int targetFriend) {
        int n = times.length;
        int[][] arrivals = new int[n][2];
        int[][] leaves = new int[n][2];
        for (int i = 0; i < n; i++) {
            arrivals[i][0] = times[i][0];
            arrivals[i][1] = i;
            leaves[i][0] = times[i][1];
            leaves[i][1] = i;
        }
        Arrays.sort(arrivals, (a, b) -> a[0] - b[0]);
        Arrays.sort(leaves, (a, b) -> a[0] - b[0]);
        Map<Integer, Integer> map = new HashMap<>();
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        for (int i = 0; i < n; i++) {
            pq.offer(i);
        }
        int j = 0;
        for (int[] arrival : arrivals) {
            while (j < n && leaves[j][0] <= arrival[0]) {
                pq.offer(map.get(leaves[j][1]));
                j++;
            }
            map.put(arrival[1], pq.poll());
            if (arrival[1] == targetFriend) {
                return map.get(targetFriend);
            }
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/the-number-of-the-smallest-unoccupied-chair/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/the-number-of-the-smallest-unoccupied-chair/description/)

Solution: [LeetCode](https://leetcode.com/articles/the-number-of-the-smallest-unoccupied-chair/)  /  [LeetCode中国](https://leetcode-cn.com/articles/the-number-of-the-smallest-unoccupied-chair/)

[回到目录](../README.md)