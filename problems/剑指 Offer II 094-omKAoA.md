# 剑指 Offer II 094. omKAoA | 最少回文分割

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个字符串 <code>s</code>，请将 <code>s</code> 分割成一些子串，使每个子串都是回文串。</p>

<p>返回符合要求的 <strong>最少分割次数</strong> 。</p>

<div class="original__bRMd">
<div>
<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = &quot;aab&quot;
<strong>输出：</strong>1
<strong>解释：</strong>只需一次分割就可将&nbsp;s<em> </em>分割成 [&quot;aa&quot;,&quot;b&quot;] 这样两个回文子串。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = &quot;a&quot;
<strong>输出：</strong>0
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = &quot;ab&quot;
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> 仅由小写英文字母组成</li>
</ul>
</div>
</div>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 132&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/palindrome-partitioning-ii/">https://leetcode-cn.com/problems/palindrome-partitioning-ii/</a></p>




## Solution

Language: **java**  /  Runtime: 1108 ms

```java
class Solution {
    public int minCut(String s) {
        int n = s.length();
        int[] dp = new int[n+1];
        dp[0]=0;
        for(int i=1;i<=n;i++){
            dp[i]=i;
            for(int j=0;j<i;j++){
                if(valid(s,j,i-1)){
                    dp[i]=Math.min(dp[i],dp[j]+1);
                }
            }
        }
        return dp[n]-1;
    }

    public boolean valid(String s,int l,int r){
        while(l<r){
            if(s.charAt(l)!=s.charAt(r)){
                return false;
            }
            l++;
            r--;
        }
        return true;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/omKAoA/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/omKAoA/description/)

Solution: [LeetCode](https://leetcode.com/articles/omKAoA/)  /  [LeetCode中国](https://leetcode-cn.com/articles/omKAoA/)

[回到目录](../README.md)