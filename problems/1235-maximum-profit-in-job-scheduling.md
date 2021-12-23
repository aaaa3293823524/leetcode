# 1235. maximum-profit-in-job-scheduling | 规划兼职工作

## Question description

<!--If you want to use the English description, use <p>We have <code>n</code> jobs, where every job is scheduled to be done from <code>startTime[i]</code> to <code>endTime[i]</code>, obtaining a profit of <code>profit[i]</code>.</p>

<p>You&#39;re given the <code>startTime</code>, <code>endTime</code> and <code>profit</code> arrays, return the maximum profit you can take such that there are no two jobs in the subset with overlapping time range.</p>

<p>If you choose a job that ends at time <code>X</code> you will be able to start another job that starts at time <code>X</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/10/10/sample1_1584.png" style="width: 380px; height: 154px;" /></strong></p>

<pre>
<strong>Input:</strong> startTime = [1,2,3,3], endTime = [3,4,5,6], profit = [50,10,40,70]
<strong>Output:</strong> 120
<strong>Explanation:</strong> The subset chosen is the first and fourth job. 
Time range [1-3]+[3-6] , we get profit of 120 = 50 + 70.
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/10/10/sample22_1584.png" style="width: 600px; height: 112px;" /> </strong></p>

<pre>
<strong>Input:</strong> startTime = [1,2,3,4,6], endTime = [3,5,10,6,9], profit = [20,20,100,70,60]
<strong>Output:</strong> 150
<strong>Explanation:</strong> The subset chosen is the first, fourth and fifth job. 
Profit obtained 150 = 20 + 70 + 60.
</pre>

<p><strong>Example 3:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/10/10/sample3_1584.png" style="width: 400px; height: 112px;" /></strong></p>

<pre>
<strong>Input:</strong> startTime = [1,1,1], endTime = [2,3,4], profit = [5,6,4]
<strong>Output:</strong> 6
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= startTime.length == endTime.length == profit.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= startTime[i] &lt; endTime[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= profit[i] &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>你打算利用空闲时间来做兼职工作赚些零花钱。</p>

<p>这里有&nbsp;<code>n</code>&nbsp;份兼职工作，每份工作预计从&nbsp;<code>startTime[i]</code>&nbsp;开始到&nbsp;<code>endTime[i]</code>&nbsp;结束，报酬为&nbsp;<code>profit[i]</code>。</p>

<p>给你一份兼职工作表，包含开始时间&nbsp;<code>startTime</code>，结束时间&nbsp;<code>endTime</code>&nbsp;和预计报酬&nbsp;<code>profit</code>&nbsp;三个数组，请你计算并返回可以获得的最大报酬。</p>

<p>注意，时间上出现重叠的 2 份工作不能同时进行。</p>

<p>如果你选择的工作在时间&nbsp;<code>X</code>&nbsp;结束，那么你可以立刻进行在时间&nbsp;<code>X</code>&nbsp;开始的下一份工作。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/10/19/sample1_1584.png" style="width: 300px;"></strong></p>

<pre><strong>输入：</strong>startTime = [1,2,3,3], endTime = [3,4,5,6], profit = [50,10,40,70]
<strong>输出：</strong>120
<strong>解释：
</strong>我们选出第 1 份和第 4 份工作， 
时间范围是 [1-3]+[3-6]，共获得报酬 120 = 50 + 70。
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/10/19/sample22_1584.png" style="height: 112px; width: 600px;"> </strong></p>

<pre><strong>输入：</strong>startTime = [1,2,3,4,6], endTime = [3,5,10,6,9], profit = [20,20,100,70,60]
<strong>输出：</strong>150
<strong>解释：
</strong>我们选择第 1，4，5 份工作。 
共获得报酬 150 = 20 + 70 + 60。
</pre>

<p><strong>示例 3：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/10/19/sample3_1584.png" style="height: 112px; width: 400px;"></strong></p>

<pre><strong>输入：</strong>startTime = [1,1,1], endTime = [2,3,4], profit = [5,6,4]
<strong>输出：</strong>6
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= startTime.length == endTime.length ==&nbsp;profit.length&nbsp;&lt;= 5 * 10^4</code></li>
	<li><code>1 &lt;=&nbsp;startTime[i] &lt;&nbsp;endTime[i] &lt;= 10^9</code></li>
	<li><code>1 &lt;=&nbsp;profit[i] &lt;= 10^4</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 22 ms

```java
class Solution {
    public int jobScheduling(int[] startTime, int[] endTime, int[] profit) {
        int [][]events= new int[startTime.length][3];
        for(int i=0;i<startTime.length;i++){
            events[i][0]=startTime[i];
            events[i][1]=endTime[i];
            events[i][2]=profit[i];
        }
        Arrays.sort(events,new Comparator<int[]>() {
        public int compare(int[] a, int[] b){
            return a[1]-b[1];
        }});
        int g[]=new int[events.length];  //做第i个工作最大报酬
        for(int i=0;i<events.length;i++){
            int left = 0;
            int right = i-1;
            while(left<=right){
                int middle = (left + right )/2;
                if(events[middle][1]>events[i][0]) right=middle-1;
                else left=middle+1;
            }
            g[i] = events[i][2];
            if(i>0){
                if(right>-1) g[i] = g[i] + g[right];
                g[i] = Math.max(g[i],g[i-1]);
            }
        }
        return g[startTime.length-1];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-profit-in-job-scheduling/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-profit-in-job-scheduling/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-profit-in-job-scheduling/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-profit-in-job-scheduling/)

[回到目录](../README.md)