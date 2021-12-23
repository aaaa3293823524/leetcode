﻿# 1815. maximum-number-of-groups-getting-fresh-donuts | 得到新鲜甜甜圈的最多组数

## Question description

<!--If you want to use the English description, use <p>There is a donuts shop that bakes donuts in batches of <code>batchSize</code>. They have a rule where they must serve <strong>all</strong> of the donuts of a batch before serving any donuts of the next batch. You are given an integer <code>batchSize</code> and an integer array <code>groups</code>, where <code>groups[i]</code> denotes that there is a group of <code>groups[i]</code> customers that will visit the shop. Each customer will get exactly one donut.</p>

<p>When a group visits the shop, all customers of the group must be served before serving any of the following groups. A group will be happy if they all get fresh donuts. That is, the first customer of the group does not receive a donut that was left over from the previous group.</p>

<p>You can freely rearrange the ordering of the groups. Return <em>the <strong>maximum</strong> possible number of happy groups after rearranging the groups.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> batchSize = 3, groups = [1,2,3,4,5,6]
<strong>Output:</strong> 4
<strong>Explanation:</strong> You can arrange the groups as [6,2,4,5,1,3]. Then the 1<sup>st</sup>, 2<sup>nd</sup>, 4<sup>th</sup>, and 6<sup>th</sup> groups will be happy.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> batchSize = 4, groups = [1,3,2,5,2,2,1,6]
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= batchSize &lt;= 9</code></li>
	<li><code>1 &lt;= groups.length &lt;= 30</code></li>
	<li><code>1 &lt;= groups[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>有一个甜甜圈商店，每批次都烤 <code>batchSize</code> 个甜甜圈。这个店铺有个规则，就是在烤一批新的甜甜圈时，之前 <strong>所有</strong> 甜甜圈都必须已经全部销售完毕。给你一个整数 <code>batchSize</code> 和一个整数数组 <code>groups</code> ，数组中的每个整数都代表一批前来购买甜甜圈的顾客，其中 <code>groups[i]</code> 表示这一批顾客的人数。每一位顾客都恰好只要一个甜甜圈。</p>

<p>当有一批顾客来到商店时，他们所有人都必须在下一批顾客来之前购买完甜甜圈。如果一批顾客中第一位顾客得到的甜甜圈不是上一组剩下的，那么这一组人都会很开心。</p>

<p>你可以随意安排每批顾客到来的顺序。请你返回在此前提下，<strong>最多</strong> 有多少组人会感到开心。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>batchSize = 3, groups = [1,2,3,4,5,6]
<b>输出：</b>4
<b>解释：</b>你可以将这些批次的顾客顺序安排为 [6,2,4,5,1,3] 。那么第 1，2，4，6 组都会感到开心。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>batchSize = 4, groups = [1,3,2,5,2,2,1,6]
<b>输出：</b>4
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= batchSize <= 9</code></li>
	<li><code>1 <= groups.length <= 30</code></li>
	<li><code>1 <= groups[i] <= 10<sup>9</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 771 ms

```java
class Solution {

    Map<Integer, Integer> dp = new HashMap<>();
    public int maxHappyGroups(int batchSize, int[] groups) {
        boolean[] vis = new boolean[groups.length];
        int[] counts = new int[9];
        int result = 0;
        for (int i = 0; i < groups.length;i++) {
            groups[i] %= batchSize;

            counts[groups[i]]++;
        }
        Arrays.sort(groups);


        result +=  dfs(vis, groups, batchSize, -1, 0);
        System.out.println("size=" + dp.size());
        System.out.println("useTime=" + useTime + "ms");
        return result;
    }

    long useTime = 0;


    public int dfs(boolean[] vis, int[] groups, int batchSize, int sum, int stateCode) {
        int result = 0;
        if (dp.containsKey(stateCode)) {
            return dp.get(stateCode);
        }

        if (sum != -1 && sum % batchSize == 0) {
            result++;
        }
        if (sum == -1) {
            sum = 0;
        }

        int max = 0;
        for (int i = 0;i<groups.length;i++) {
            if (vis[i]) {
                continue;
            }
            // 前一个点没走过，且和自己的值相等，则不走，因为明明可以选前面的
            if (i-1 >= 0 && groups[i-1] == groups[i] && !vis[i-1]) {
                continue;
            }

            vis[i] = true;
            stateCode += (1<<i);
            int nextResult = dfs(vis, groups, batchSize, sum + groups[i], stateCode);
            stateCode -= (1<<i);
            vis[i] = false;
            max = Math.max(nextResult, max);
        }
        if (max == 0 && result == 0) {
            max = 1;
        }

        dp.put(stateCode, max + result);
        return max + result;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-number-of-groups-getting-fresh-donuts/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-number-of-groups-getting-fresh-donuts/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-number-of-groups-getting-fresh-donuts/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-number-of-groups-getting-fresh-donuts/)

[回到目录](../README.md)