# 1936. add-minimum-number-of-rungs | 新增的最少台阶数

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>strictly increasing</strong> integer array <code>rungs</code> that represents the <strong>height</strong> of rungs on a ladder. You are currently on the <strong>floor</strong> at height <code>0</code>, and you want to reach the last rung.</p>

<p>You are also given an integer <code>dist</code>. You can only climb to the next highest rung if the distance between where you are currently at (the floor or on a rung) and the next rung is <strong>at most</strong> <code>dist</code>. You are able to insert rungs at any positive <strong>integer</strong> height if a rung is not already there.</p>

<p>Return <em>the <strong>minimum</strong> number of rungs that must be added to the ladder in order for you to climb to the last rung.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> rungs = [1,3,5,10], dist = 2
<strong>Output:</strong> 2
<strong>Explanation:
</strong>You currently cannot reach the last rung.
Add rungs at heights 7 and 8 to climb this ladder. 
The ladder will now have rungs at [1,3,5,<u>7</u>,<u>8</u>,10].
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> rungs = [3,6,8,10], dist = 3
<strong>Output:</strong> 0
<strong>Explanation:</strong>
This ladder can be climbed without adding additional rungs.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> rungs = [3,4,6,7], dist = 2
<strong>Output:</strong> 1
<strong>Explanation:</strong>
You currently cannot reach the first rung from the ground.
Add a rung at height 1 to climb this ladder.
The ladder will now have rungs at [<u>1</u>,3,4,6,7].
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> rungs = [5], dist = 10
<strong>Output:</strong> 0
<strong>Explanation:</strong>
This ladder can be climbed without adding additional rungs.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= rungs.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= rungs[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= dist &lt;= 10<sup>9</sup></code></li>
	<li><code>rungs</code> is <strong>strictly increasing</strong>.</li>
</ul>
 instead-->
<p>给你一个 <strong>严格递增</strong> 的整数数组 <code>rungs</code> ，用于表示梯子上每一台阶的 <strong>高度</strong> 。当前你正站在高度为 <code>0</code> 的地板上，并打算爬到最后一个台阶。</p>

<p>另给你一个整数 <code>dist</code> 。每次移动中，你可以到达下一个距离你当前位置（地板或台阶）<strong>不超过</strong> <code>dist</code> 高度的台阶。当然，你也可以在任何正 <strong>整数</strong> 高度处插入尚不存在的新台阶。</p>

<p>返回爬到最后一阶时必须添加到梯子上的 <strong>最少</strong> 台阶数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>rungs = [1,3,5,10], dist = 2
<strong>输出：</strong>2
<strong>解释：
</strong>现在无法到达最后一阶。
在高度为 7 和 8 的位置增设新的台阶，以爬上梯子。 
梯子在高度为 [1,3,5,<strong><em>7</em></strong>,<strong><em>8</em></strong>,10] 的位置上有台阶。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>rungs = [3,6,8,10], dist = 3
<strong>输出：</strong>0
<strong>解释：</strong>
这个梯子无需增设新台阶也可以爬上去。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>rungs = [3,4,6,7], dist = 2
<strong>输出：</strong>1
<strong>解释：</strong>
现在无法从地板到达梯子的第一阶。 
在高度为 1 的位置增设新的台阶，以爬上梯子。 
梯子在高度为 [<strong><em>1</em></strong>,3,4,6,7] 的位置上有台阶。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>rungs = [5], dist = 10
<strong>输出：</strong>0
<strong>解释：</strong>这个梯子无需增设新台阶也可以爬上去。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= rungs.length <= 10<sup>5</sup></code></li>
	<li><code>1 <= rungs[i] <= 10<sup>9</sup></code></li>
	<li><code>1 <= dist <= 10<sup>9</sup></code></li>
	<li><code>rungs</code> <strong>严格递增</strong></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int addRungs(int[] rungs, int dist) {
        int cur=0;
        int count=0;
        for(int i=0;i<rungs.length;i++) {
            // while(cur+dist<rungs[i]) {
            //     cur=cur+dist;
            //     count++;
            // }
            count+=(rungs[i]-cur-1)/dist;
            cur=rungs[i];
        }
        return count;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-minimum-number-of-rungs/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-minimum-number-of-rungs/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-minimum-number-of-rungs/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-minimum-number-of-rungs/)

[回到目录](../README.md)