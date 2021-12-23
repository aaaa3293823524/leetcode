# 1984. minimum-difference-between-highest-and-lowest-of-k-scores | 学生分数的最小差值

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>0-indexed</strong> integer array <code>nums</code>, where <code>nums[i]</code> represents the score of the <code>i<sup>th</sup></code> student. You are also given an integer <code>k</code>.</p>

<p>Pick the scores of any <code>k</code> students from the array so that the <strong>difference</strong> between the <strong>highest</strong> and the <strong>lowest</strong> of the <code>k</code> scores is <strong>minimized</strong>.</p>

<p>Return <em>the <strong>minimum</strong> possible difference</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [90], k = 1
<strong>Output:</strong> 0
<strong>Explanation:</strong> There is one way to pick score(s) of one student:
- [<strong><u>90</u></strong>]. The difference between the highest and lowest score is 90 - 90 = 0.
The minimum possible difference is 0.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [9,4,1,7], k = 2
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are six ways to pick score(s) of two students:
- [<strong><u>9</u></strong>,<strong><u>4</u></strong>,1,7]. The difference between the highest and lowest score is 9 - 4 = 5.
- [<strong><u>9</u></strong>,4,<strong><u>1</u></strong>,7]. The difference between the highest and lowest score is 9 - 1 = 8.
- [<strong><u>9</u></strong>,4,1,<strong><u>7</u></strong>]. The difference between the highest and lowest score is 9 - 7 = 2.
- [9,<strong><u>4</u></strong>,<strong><u>1</u></strong>,7]. The difference between the highest and lowest score is 4 - 1 = 3.
- [9,<strong><u>4</u></strong>,1,<strong><u>7</u></strong>]. The difference between the highest and lowest score is 7 - 4 = 3.
- [9,4,<strong><u>1</u></strong>,<strong><u>7</u></strong>]. The difference between the highest and lowest score is 7 - 1 = 6.
The minimum possible difference is 2.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= nums.length &lt;= 1000</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>给你一个 <strong>下标从 0 开始</strong> 的整数数组 <code>nums</code> ，其中 <code>nums[i]</code> 表示第 <code>i</code> 名学生的分数。另给你一个整数 <code>k</code> 。</p>

<p>从数组中选出任意 <code>k</code> 名学生的分数，使这 <code>k</code> 个分数间 <strong>最高分</strong> 和 <strong>最低分</strong> 的 <strong>差值</strong> 达到<strong> 最小化</strong> 。</p>

<p>返回可能的 <strong>最小差值</strong> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [90], k = 1
<strong>输出：</strong>0
<strong>解释：</strong>选出 1 名学生的分数，仅有 1 种方法：
- [<em><strong>90</strong></em>] 最高分和最低分之间的差值是 90 - 90 = 0
可能的最小差值是 0
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [9,4,1,7], k = 2
<strong>输出：</strong>2
<strong>解释：</strong>选出 2 名学生的分数，有 6 种方法：
- [<em><strong>9</strong></em>,<em><strong>4</strong></em>,1,7] 最高分和最低分之间的差值是 9 - 4 = 5
- [<em><strong>9</strong></em>,4,<em><strong>1</strong></em>,7] 最高分和最低分之间的差值是 9 - 1 = 8
- [<em><strong>9</strong></em>,4,1,<em><strong>7</strong></em>] 最高分和最低分之间的差值是 9 - 7 = 2
- [9,<em><strong>4</strong></em>,<em><strong>1</strong></em>,7] 最高分和最低分之间的差值是 4 - 1 = 3
- [9,<em><strong>4</strong></em>,1,<em><strong>7</strong></em>] 最高分和最低分之间的差值是 7 - 4 = 3
- [9,4,<em><strong>1</strong></em>,<em><strong>7</strong></em>] 最高分和最低分之间的差值是 7 - 1 = 6
可能的最小差值是 2</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= nums.length &lt;= 1000</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 72 ms

```java
class Solution {
    public int minimumDifference(int[] nums, int k) {
        if(k==1)return 0;
        Arrays.sort(nums);
        int ans=Integer.MAX_VALUE;
        for(int i=0;i+k-1<=nums.length-1;i++) {
            System.out.println("i:"+i+"j:"+(i+k-1));
            ans=Math.min(ans, nums[i+k-1]-nums[i]);
        }
        return ans;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-difference-between-highest-and-lowest-of-k-scores/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-difference-between-highest-and-lowest-of-k-scores/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-difference-between-highest-and-lowest-of-k-scores/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-difference-between-highest-and-lowest-of-k-scores/)

[回到目录](../README.md)