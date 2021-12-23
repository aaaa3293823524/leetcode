# 763. partition-labels | 划分字母区间

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>s</code>. We want to partition the string into as many parts as possible so that each letter appears in at most one part.</p>

<p>Return <em>a list of integers representing the size of these parts</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ababcbacadefegdehijhklij&quot;
<strong>Output:</strong> [9,7,8]
<strong>Explanation:</strong>
The partition is &quot;ababcbaca&quot;, &quot;defegde&quot;, &quot;hijhklij&quot;.
This is a partition so that each letter appears in at most one part.
A partition like &quot;ababcbacadefegde&quot;, &quot;hijhklij&quot; is incorrect, because it splits s into less parts.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;eccbbbbdec&quot;
<strong>Output:</strong> [10]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 500</code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
 instead-->
<p>字符串 <code>S</code> 由小写字母组成。我们要把这个字符串划分为尽可能多的片段，同一字母最多出现在一个片段中。返回一个表示每个字符串片段的长度的列表。</p>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>S = "ababcbacadefegdehijhklij"
<strong>输出：</strong>[9,7,8]
<strong>解释：</strong>
划分结果为 "ababcbaca", "defegde", "hijhklij"。
每个字母最多出现在一个片段中。
像 "ababcbacadefegde", "hijhklij" 的划分是错误的，因为划分的片段数较少。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>S</code>的长度在<code>[1, 500]</code>之间。</li>
	<li><code>S</code>只包含小写字母 <code>'a'</code> 到 <code>'z'</code> 。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public List<Integer> partitionLabels(String s) {
         HashMap<Character, Integer>map=new HashMap<Character, Integer>();
         char[]c=s.toCharArray();
         for(int i=0;i<c.length;i++) {
             map.put(c[i],i);
         }
         List<String>list=new ArrayList<String>();
         int ans=0;
         int pre=0;
         for(int i=0;i<c.length;i++) {
             int t=map.get(c[i]);
             ans=Math.max(ans, t);
             if(ans==i) {
                 list.add(s.substring(pre,i+1));
                 ans=0;
                 pre=i+1;
             }
         }
         List<Integer>res=new ArrayList<Integer>();
         for(int i=0;i<list.size();i++) {
             res.add(list.get(i).length());
         }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/partition-labels/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/partition-labels/description/)

Solution: [LeetCode](https://leetcode.com/articles/partition-labels/)  /  [LeetCode中国](https://leetcode-cn.com/articles/partition-labels/)

[回到目录](../README.md)