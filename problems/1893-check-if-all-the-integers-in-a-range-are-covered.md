# 1893. check-if-all-the-integers-in-a-range-are-covered | 检查是否区域内所有整数都被覆盖

## Question description

<!--If you want to use the English description, use <p>You are given a 2D integer array <code>ranges</code> and two integers <code>left</code> and <code>right</code>. Each <code>ranges[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> represents an <strong>inclusive</strong> interval between <code>start<sub>i</sub></code> and <code>end<sub>i</sub></code>.</p>

<p>Return <code>true</code> <em>if each integer in the inclusive range</em> <code>[left, right]</code> <em>is covered by <strong>at least one</strong> interval in</em> <code>ranges</code>. Return <code>false</code> <em>otherwise</em>.</p>

<p>An integer <code>x</code> is covered by an interval <code>ranges[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> if <code>start<sub>i</sub> &lt;= x &lt;= end<sub>i</sub></code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> ranges = [[1,2],[3,4],[5,6]], left = 2, right = 5
<strong>Output:</strong> true
<strong>Explanation:</strong> Every integer between 2 and 5 is covered:
- 2 is covered by the first range.
- 3 and 4 are covered by the second range.
- 5 is covered by the third range.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> ranges = [[1,10],[10,20]], left = 21, right = 21
<strong>Output:</strong> false
<strong>Explanation:</strong> 21 is not covered by any range.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= ranges.length &lt;= 50</code></li>
	<li><code>1 &lt;= start<sub>i</sub> &lt;= end<sub>i</sub> &lt;= 50</code></li>
	<li><code>1 &lt;= left &lt;= right &lt;= 50</code></li>
</ul>
 instead-->
<p>给你一个二维整数数组 <code>ranges</code> 和两个整数 <code>left</code> 和 <code>right</code> 。每个 <code>ranges[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> 表示一个从 <code>start<sub>i</sub></code> 到 <code>end<sub>i</sub></code> 的 <strong>闭区间</strong> 。</p>

<p>如果闭区间 <code>[left, right]</code> 内每个整数都被 <code>ranges</code> 中 <strong>至少一个</strong> 区间覆盖，那么请你返回 <code>true</code> ，否则返回 <code>false</code> 。</p>

<p>已知区间 <code>ranges[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> ，如果整数 <code>x</code> 满足 <code>start<sub>i</sub> <= x <= end<sub>i</sub></code> ，那么我们称整数<code>x</code> 被覆盖了。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>ranges = [[1,2],[3,4],[5,6]], left = 2, right = 5
<b>输出：</b>true
<b>解释：</b>2 到 5 的每个整数都被覆盖了：
- 2 被第一个区间覆盖。
- 3 和 4 被第二个区间覆盖。
- 5 被第三个区间覆盖。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>ranges = [[1,10],[10,20]], left = 21, right = 21
<b>输出：</b>false
<b>解释：</b>21 没有被任何一个区间覆盖。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= ranges.length <= 50</code></li>
	<li><code>1 <= start<sub>i</sub> <= end<sub>i</sub> <= 50</code></li>
	<li><code>1 <= left <= right <= 50</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 11 ms

```java
class Solution {
    public boolean isCovered(int[][] ranges, int left, int right) {
        Deque<int[]>stack=new LinkedList<int[]>();
        Arrays.sort(ranges,(a,b)->a[0]-b[0]);
        stack.push(ranges[0]);
        for(int i=1;i<ranges.length;i++) {
            //System.out.println((ranges[i][0]-1)+"::::"+stack.peek()[1]);
            if((ranges[i][0]-1)<=stack.peek()[1]) {
                int[] t=stack.pop();
                stack.push(new int[] {t[0],Math.max(ranges[i][1],t[1])});
            }else {
                stack.push(ranges[i]);
            }
        }
        while(!stack.isEmpty()) {
            int[] t=stack.pop();
            System.out.println(t[0]+":"+t[1]);
            if(t[0]<=left&&right<=t[1])return true;
        }
        return false;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/check-if-all-the-integers-in-a-range-are-covered/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/check-if-all-the-integers-in-a-range-are-covered/description/)

Solution: [LeetCode](https://leetcode.com/articles/check-if-all-the-integers-in-a-range-are-covered/)  /  [LeetCode中国](https://leetcode-cn.com/articles/check-if-all-the-integers-in-a-range-are-covered/)

[回到目录](../README.md)