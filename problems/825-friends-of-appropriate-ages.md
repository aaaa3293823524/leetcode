﻿# 825. friends-of-appropriate-ages | 适龄的朋友

## Question description

<!--If you want to use the English description, use <p>There are <code>n</code> persons on a social media website. You are given an integer array <code>ages</code> where <code>ages[i]</code> is the age of the <code>i<sup>th</sup></code> person.</p>

<p>A Person <code>x</code> will not send a friend request to a person <code>y</code> (<code>x != y</code>) if any of the following conditions is true:</p>

<ul>
	<li><code>age[y] &lt;= 0.5 * age[x] + 7</code></li>
	<li><code>age[y] &gt; age[x]</code></li>
	<li><code>age[y] &gt; 100 &amp;&amp; age[x] &lt; 100</code></li>
</ul>

<p>Otherwise, <code>x</code> will send a friend request to <code>y</code>.</p>

<p>Note that if <code>x</code> sends a request to <code>y</code>, <code>y</code> will not necessarily send a request to <code>x</code>. Also, a person will not send a friend request to themself.</p>

<p>Return <em>the total number of friend requests made</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> ages = [16,16]
<strong>Output:</strong> 2
<strong>Explanation:</strong> 2 people friend request each other.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> ages = [16,17,18]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Friend requests are made 17 -&gt; 16, 18 -&gt; 17.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> ages = [20,30,100,110,120]
<strong>Output:</strong> 3
<strong>Explanation:</strong> Friend requests are made 110 -&gt; 100, 120 -&gt; 110, 120 -&gt; 100.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == ages.length</code></li>
	<li><code>1 &lt;= n &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= ages[i] &lt;= 120</code></li>
</ul>
 instead-->
<p>在社交媒体网站上有 <code>n</code> 个用户。给你一个整数数组 <code>ages</code> ，其中 <code>ages[i]</code> 是第 <code>i</code> 个用户的年龄。</p>

<p>如果下述任意一个条件为真，那么用户 <code>x</code> 将不会向用户 <code>y</code>（<code>x != y</code>）发送好友请求：</p>

<ul>
	<li><code>age[y] &lt;= 0.5 * age[x] + 7</code></li>
	<li><code>age[y] &gt; age[x]</code></li>
	<li><code>age[y] &gt; 100 &amp;&amp; age[x] &lt; 100</code></li>
</ul>

<p>否则，<code>x</code> 将会向 <code>y</code> 发送一条好友请求。</p>

<p>注意，如果 <code>x</code> 向 <code>y</code> 发送一条好友请求，<code>y</code> 不必也向 <code>x</code> 发送一条好友请求。另外，用户不会向自己发送好友请求。</p>

<p>返回在该社交媒体网站上产生的好友请求总数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>ages = [16,16]
<strong>输出：</strong>2
<strong>解释：</strong>2 人互发好友请求。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>ages = [16,17,18]
<strong>输出：</strong>2
<strong>解释：</strong>产生的好友请求为 17 -&gt; 16 ，18 -&gt; 17 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>ages = [20,30,100,110,120]
<strong>输出：</strong>3
<strong>解释：</strong>产生的好友请求为 110 -&gt; 100 ，120 -&gt; 110 ，120 -&gt; 100 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == ages.length</code></li>
	<li><code>1 &lt;= n &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= ages[i] &lt;= 120</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public int numFriendRequests(int[] ages) {
        int[] count = new int[121];
        for (int age: ages) count[age]++;

        int ans = 0;
        for (int ageA = 0; ageA <= 120; ageA++) {
            int countA = count[ageA];
            for (int ageB = 0; ageB <= 120; ageB++) {
                int countB = count[ageB];
                if (ageA * 0.5 + 7 >= ageB) continue;
                if (ageA < ageB) continue;
                if (ageA < 100 && 100 < ageB) continue;
                ans += countA * countB;
                if (ageA == ageB) ans -= countA;
            }
        }

        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/friends-of-appropriate-ages/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/friends-of-appropriate-ages/description/)

Solution: [LeetCode](https://leetcode.com/articles/friends-of-appropriate-ages/)  /  [LeetCode中国](https://leetcode-cn.com/articles/friends-of-appropriate-ages/)

[回到目录](../README.md)