# 506. relative-ranks | 相对名次

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>score</code> of size <code>n</code>, where <code>score[i]</code> is the score of the <code>i<sup>th</sup></code> athlete in a competition. All the scores are guaranteed to be <strong>unique</strong>.</p>

<p>The athletes are <strong>placed</strong> based on their scores, where the <code>1<sup>st</sup></code> place athlete has the highest score, the <code>2<sup>nd</sup></code> place athlete has the <code>2<sup>nd</sup></code> highest score, and so on. The placement of each athlete determines their rank:</p>

<ul>
	<li>The <code>1<sup>st</sup></code> place athlete&#39;s rank is <code>&quot;Gold Medal&quot;</code>.</li>
	<li>The <code>2<sup>nd</sup></code> place athlete&#39;s rank is <code>&quot;Silver Medal&quot;</code>.</li>
	<li>The <code>3<sup>rd</sup></code> place athlete&#39;s rank is <code>&quot;Bronze Medal&quot;</code>.</li>
	<li>For the <code>4<sup>th</sup></code> place to the <code>n<sup>th</sup></code> place athlete, their rank is their placement number (i.e., the <code>x<sup>th</sup></code> place athlete&#39;s rank is <code>&quot;x&quot;</code>).</li>
</ul>

<p>Return an array <code>answer</code> of size <code>n</code> where <code>answer[i]</code> is the <strong>rank</strong> of the <code>i<sup>th</sup></code> athlete.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> score = [5,4,3,2,1]
<strong>Output:</strong> [&quot;Gold Medal&quot;,&quot;Silver Medal&quot;,&quot;Bronze Medal&quot;,&quot;4&quot;,&quot;5&quot;]
<strong>Explanation:</strong> The placements are [1<sup>st</sup>, 2<sup>nd</sup>, 3<sup>rd</sup>, 4<sup>th</sup>, 5<sup>th</sup>].</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> score = [10,3,8,9,4]
<strong>Output:</strong> [&quot;Gold Medal&quot;,&quot;5&quot;,&quot;Bronze Medal&quot;,&quot;Silver Medal&quot;,&quot;4&quot;]
<strong>Explanation:</strong> The placements are [1<sup>st</sup>, 5<sup>th</sup>, 3<sup>rd</sup>, 2<sup>nd</sup>, 4<sup>th</sup>].

</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == score.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= score[i] &lt;= 10<sup>6</sup></code></li>
	<li>All the values in <code>score</code> are <strong>unique</strong>.</li>
</ul>
 instead-->
<p>给你一个长度为 <code>n</code> 的整数数组 <code>score</code> ，其中 <code>score[i]</code> 是第 <code>i</code> 位运动员在比赛中的得分。所有得分都 <strong>互不相同</strong> 。</p>

<p>运动员将根据得分 <strong>决定名次</strong> ，其中名次第 <code>1</code> 的运动员得分最高，名次第 <code>2</code> 的运动员得分第 <code>2</code> 高，依此类推。运动员的名次决定了他们的获奖情况：</p>

<ul>
	<li>名次第 <code>1</code> 的运动员获金牌 <code>"Gold Medal"</code> 。</li>
	<li>名次第 <code>2</code> 的运动员获银牌 <code>"Silver Medal"</code> 。</li>
	<li>名次第 <code>3</code> 的运动员获铜牌 <code>"Bronze Medal"</code> 。</li>
	<li>从名次第 <code>4</code> 到第 <code>n</code> 的运动员，只能获得他们的名次编号（即，名次第 <code>x</code> 的运动员获得编号 <code>"x"</code>）。</li>
</ul>

<p>使用长度为 <code>n</code> 的数组 <code>answer</code> 返回获奖，其中 <code>answer[i]</code> 是第 <code>i</code> 位运动员的获奖情况。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>score = [5,4,3,2,1]
<strong>输出：</strong>["Gold Medal","Silver Medal","Bronze Medal","4","5"]
<strong>解释：</strong>名次为 [1<sup>st</sup>, 2<sup>nd</sup>, 3<sup>rd</sup>, 4<sup>th</sup>, 5<sup>th</sup>] 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>score = [10,3,8,9,4]
<strong>输出：</strong>["Gold Medal","5","Bronze Medal","Silver Medal","4"]
<strong>解释：</strong>名次为 [1<sup>st</sup>, 5<sup>th</sup>, 3<sup>rd</sup>, 2<sup>nd</sup>, 4<sup>th</sup>] 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == score.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= score[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>score</code> 中的所有值 <strong>互不相同</strong></li>
</ul>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public String[] findRelativeRanks(int[] score) {
        int n = score.length;
        String[] ans = new String[n];
        int[] clone = Arrays.copyOf(score, n); //复制score数组并进行排序
        Arrays.sort(clone);
        for (int i = 0; i < score.length; i++) {
            int rank = n - Arrays.binarySearch(clone, score[i]); //n - 排序后的下标 == 名次
            if (rank == 1) ans[i] = "Gold Medal";
            else if (rank == 2) ans[i] = "Silver Medal";
            else if (rank == 3) ans[i] = "Bronze Medal";
            else ans[i] = Integer.toString(rank);
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/relative-ranks/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/relative-ranks/description/)

Solution: [LeetCode](https://leetcode.com/articles/relative-ranks/)  /  [LeetCode中国](https://leetcode-cn.com/articles/relative-ranks/)

[回到目录](../README.md)