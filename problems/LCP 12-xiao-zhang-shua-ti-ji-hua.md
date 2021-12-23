# LCP 12. xiao-zhang-shua-ti-ji-hua | 小张刷题计划

## Question description

<!--If you want to use the English description, use  instead-->
<p>为了提高自己的代码能力，小张制定了 <code>LeetCode</code> 刷题计划，他选中了 <code>LeetCode</code> 题库中的 <code>n</code> 道题，编号从 <code>0</code> 到 <code>n-1</code>，并计划在 <code>m</code> 天内<strong>按照题目编号顺序</strong>刷完所有的题目（注意，小张不能用多天完成同一题）。</p>

<p>在小张刷题计划中，小张需要用 <code>time[i]</code> 的时间完成编号 <code>i</code> 的题目。此外，小张还可以使用场外求助功能，通过询问他的好朋友小杨题目的解法，可以省去该题的做题时间。为了防止&ldquo;小张刷题计划&rdquo;变成&ldquo;小杨刷题计划&rdquo;，小张每天最多使用一次求助。</p>

<p>我们定义 <code>m</code> 天中做题时间最多的一天耗时为 <code>T</code>（小杨完成的题目不计入做题总时间）。请你帮小张求出最小的 <code>T</code>是多少。</p>

<p><strong>示例 1：</strong></p>

<blockquote>
<p>输入：<code>time = [1,2,3,3], m = 2</code></p>

<p>输出：<code>3</code></p>

<p>解释：第一天小张完成前三题，其中第三题找小杨帮忙；第二天完成第四题，并且找小杨帮忙。这样做题时间最多的一天花费了 3 的时间，并且这个值是最小的。</p>
</blockquote>

<p><strong>示例 2：</strong></p>

<blockquote>
<p>输入：<code>time = [999,999,999], m = 4</code></p>

<p>输出：<code>0</code></p>

<p>解释：在前三天中，小张每天求助小杨一次，这样他可以在三天内完成所有的题目并不花任何时间。</p>
</blockquote>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>1 &lt;= time.length &lt;= 10^5</code></li>
	<li><code>1 &lt;= time[i] &lt;= 10000</code></li>
	<li><code>1 &lt;= m &lt;= 1000</code></li>
</ul>


## Note

题意概述

给定一个数组，将其划分成 MM 份，使得每份元素之和最大值最小，每份可以任意减去其中一个元素。



题解

如果不考虑每份可以任意减去一个元素，就是一个经典的二分问题，具有单调最优的性质：如果最大值为 tt 可以满足条件划分，那么最大值为 t+1t+1 也可以。所以就直接二分最大值 tt，找到最小满足条件的 tt 即可。



本题加了一个条件：每份可以删除任意一个数组。为了能够让最大值最小，显然每份中删去的一定是最大元素，所以在二分判定可行性时，维护当前序列的最大值，然后记录删除最大值的结果，也就是说二分的判定是：是否可以让每组删除最大值之后，总和都小于等于 tt。






## Solution

Language: **cpp**  /  Runtime: 172 ms

```cpp
class Solution {
public:
    bool Check(int limit, vector<int> cost, int day) {
      // 每组划分 limit 的最大和，贪心划分看有多少组
        int useday, totaltime, maxtime;
        useday = 1; totaltime = maxtime = 0;
        for (int i=0; i<cost.size(); ++i) {
            int nexttime = min(maxtime, cost[i]);
            if (nexttime + totaltime <= limit) {
                totaltime += nexttime;
                maxtime = max(maxtime, cost[i]);
            } else {
                ++useday;
                totaltime = 0;
                maxtime = cost[i];
            }
        }
        return (useday <= day);
    }
    int minTime(vector<int>& time, int m) {
        int left, right, middle;
        left = right = 0;
        for (int i=0; i<time.size(); ++i) {
            right += time[i];
        }
        while (left <= right) {
            middle = (left + right) >> 1;
            if (Check(middle, time, m)) right = middle - 1;
            else left = middle + 1;
        }
        return left;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/xiao-zhang-shua-ti-ji-hua/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/xiao-zhang-shua-ti-ji-hua/description/)

Solution: [LeetCode](https://leetcode.com/articles/xiao-zhang-shua-ti-ji-hua/)  /  [LeetCode中国](https://leetcode-cn.com/articles/xiao-zhang-shua-ti-ji-hua/)

[回到目录](../README.md)