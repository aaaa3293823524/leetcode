# 646. maximum-length-of-pair-chain | 最长数对链

## Question description

<!--If you want to use the English description, use <p>You are given an array of <code>n</code> pairs <code>pairs</code> where <code>pairs[i] = [left<sub>i</sub>, right<sub>i</sub>]</code> and <code>left<sub>i</sub> &lt; right<sub>i</sub></code>.</p>

<p>A pair <code>p2 = [c, d]</code> <strong>follows</strong> a pair <code>p1 = [a, b]</code> if <code>b &lt; c</code>. A <strong>chain</strong> of pairs can be formed in this fashion.</p>

<p>Return <em>the length longest chain which can be formed</em>.</p>

<p>You do not need to use up all the given intervals. You can select pairs in any order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> pairs = [[1,2],[2,3],[3,4]]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The longest chain is [1,2] -&gt; [3,4].
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> pairs = [[1,2],[7,8],[4,5]]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The longest chain is [1,2] -&gt; [4,5] -&gt; [7,8].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == pairs.length</code></li>
	<li><code>1 &lt;= n &lt;= 1000</code></li>
	<li><code>-1000 &lt;= left<sub>i</sub> &lt; right<sub>i</sub> &lt;= 1000</code></li>
</ul>
 instead-->
<p>给出 <code>n</code> 个数对。 在每一个数对中，第一个数字总是比第二个数字小。</p>

<p>现在，我们定义一种跟随关系，当且仅当 <code>b < c</code> 时，数对<code>(c, d)</code> 才可以跟在 <code>(a, b)</code> 后面。我们用这种形式来构造一个数对链。</p>

<p>给定一个数对集合，找出能够形成的最长数对链的长度。你不需要用到所有的数对，你可以以任何顺序选择其中的一些数对来构造。</p>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>[[1,2], [2,3], [3,4]]
<strong>输出：</strong>2
<strong>解释：</strong>最长的数对链是 [1,2] -> [3,4]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>给出数对的个数在 <code>[1, 1000]</code> 范围内。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 42 ms

```java
class Solution {
    public int findLongestChain(int[][] pairs) {
         Arrays.sort(pairs,(a,b)->a[0]-b[0]);
         int n=pairs.length;
         int[]dp=new int[n];
        dp[0]=1;
         for(int i=1;i<n;i++) {
             // if(pairs[i][0]>pairs[i-1][1]){
            //      dp[i]=dp[i-1]+1;
             // }else {
             //     dp[i]=dp[i-1];
             // }
             int ans=0;
             for(int j=0;j<i;j++){
                 if(pairs[i][0]>pairs[j][1]){
                     dp[i]=dp[j]+1;
                 }else{
                     dp[i]=dp[j];
                 }
                 ans=Math.max(ans,dp[i]);
             }
             dp[i]=ans;
         }

        return dp[n-1];  
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-length-of-pair-chain/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-length-of-pair-chain/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-length-of-pair-chain/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-length-of-pair-chain/)

[回到目录](../README.md)