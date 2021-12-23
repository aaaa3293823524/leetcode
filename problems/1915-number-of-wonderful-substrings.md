# 1915. number-of-wonderful-substrings | 最美子字符串的数目

## Question description

<!--If you want to use the English description, use <p>A <strong>wonderful</strong> string is a string where <strong>at most one</strong> letter appears an <strong>odd</strong> number of times.</p>

<ul>
	<li>For example, <code>&quot;ccjjc&quot;</code> and <code>&quot;abab&quot;</code> are wonderful, but <code>&quot;ab&quot;</code> is not.</li>
</ul>

<p>Given a string <code>word</code> that consists of the first ten lowercase English letters (<code>&#39;a&#39;</code> through <code>&#39;j&#39;</code>), return <em>the <strong>number of wonderful non-empty substrings</strong> in </em><code>word</code><em>. If the same substring appears multiple times in </em><code>word</code><em>, then count <strong>each occurrence</strong> separately.</em></p>

<p>A <strong>substring</strong> is a contiguous sequence of characters in a string.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;aba&quot;
<strong>Output:</strong> 4
<strong>Explanation:</strong> The four wonderful substrings are underlined below:
- &quot;<u><strong>a</strong></u>ba&quot; -&gt; &quot;a&quot;
- &quot;a<u><strong>b</strong></u>a&quot; -&gt; &quot;b&quot;
- &quot;ab<u><strong>a</strong></u>&quot; -&gt; &quot;a&quot;
- &quot;<u><strong>aba</strong></u>&quot; -&gt; &quot;aba&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;aabb&quot;
<strong>Output:</strong> 9
<strong>Explanation:</strong> The nine wonderful substrings are underlined below:
- &quot;<strong><u>a</u></strong>abb&quot; -&gt; &quot;a&quot;
- &quot;<u><strong>aa</strong></u>bb&quot; -&gt; &quot;aa&quot;
- &quot;<u><strong>aab</strong></u>b&quot; -&gt; &quot;aab&quot;
- &quot;<u><strong>aabb</strong></u>&quot; -&gt; &quot;aabb&quot;
- &quot;a<u><strong>a</strong></u>bb&quot; -&gt; &quot;a&quot;
- &quot;a<u><strong>abb</strong></u>&quot; -&gt; &quot;abb&quot;
- &quot;aa<u><strong>b</strong></u>b&quot; -&gt; &quot;b&quot;
- &quot;aa<u><strong>bb</strong></u>&quot; -&gt; &quot;bb&quot;
- &quot;aab<u><strong>b</strong></u>&quot; -&gt; &quot;b&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;he&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The two wonderful substrings are underlined below:
- &quot;<b><u>h</u></b>e&quot; -&gt; &quot;h&quot;
- &quot;h<strong><u>e</u></strong>&quot; -&gt; &quot;e&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word.length &lt;= 10<sup>5</sup></code></li>
	<li><code>word</code> consists of lowercase English letters from <code>&#39;a&#39;</code>&nbsp;to <code>&#39;j&#39;</code>.</li>
</ul> instead-->
<p>如果某个字符串中 <strong>至多一个</strong> 字母出现 <strong>奇数</strong> 次，则称其为 <strong>最美</strong> 字符串。</p>

<ul>
	<li>例如，<code>"ccjjc"</code> 和 <code>"abab"</code> 都是最美字符串，但 <code>"ab"</code> 不是。</li>
</ul>

<p>给你一个字符串 <code>word</code> ，该字符串由前十个小写英文字母组成（<code>'a'</code> 到 <code>'j'</code>）。请你返回 <code>word</code> 中 <strong>最美非空子字符串</strong> 的数目<em>。</em>如果同样的子字符串在<em> </em><code>word</code> 中出现多次，那么应当对 <strong>每次出现</strong> 分别计数<em>。</em></p>

<p><strong>子字符串</strong> 是字符串中的一个连续字符序列。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>word = "aba"
<strong>输出：</strong>4
<strong>解释：</strong>4 个最美子字符串如下所示：
- "<strong>a</strong>ba" -> "a"
- "a<strong>b</strong>a" -> "b"
- "ab<strong>a</strong>" -> "a"
- "<strong>aba</strong>" -> "aba"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>word = "aabb"
<strong>输出：</strong>9
<strong>解释：</strong>9 个最美子字符串如下所示：
- "<strong>a</strong>abb" -> "a"
- "<strong>aa</strong>bb" -> "aa"
- "<strong>aab</strong>b" -> "aab"
- "<strong>aabb</strong>" -> "aabb"
- "a<strong>a</strong>bb" -> "a"
- "a<strong>abb</strong>" -> "abb"
- "aa<strong>b</strong>b" -> "b"
- "aa<strong>bb</strong>" -> "bb"
- "aab<strong>b</strong>" -> "b"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>word = "he"
<strong>输出：</strong>2
<strong>解释：</strong>2 个最美子字符串如下所示：
- "<b>h</b>e" -> "h"
- "h<strong>e</strong>" -> "e"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= word.length <= 10<sup>5</sup></code></li>
	<li><code>word</code> 由从 <code>'a'</code> 到 <code>'j'</code> 的小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 22 ms

```java
class Solution {
    public long wonderfulSubstrings(String word) {
        long ans = 0;
        int mask = 0;
        long[] freq = new long[1 << 10];
        freq[0] = 1;
        for (char c : word.toCharArray()) {
            int index = c - 'a';
            mask ^= (1 << index);
            ans += freq[mask];
            for (int i = 0; i < 10; i++) {
        ans += freq[mask ^ (1 << i)];
        }
            freq[mask]++;
        }
        return ans;
    }
}



// class Solution {
//     public long wonderfulSubstrings(String word) {
//         long sum=0;
//         for(int i=0;i<word.length();i++) {
//             for(int j=i+1;j<=word.length();j++) {
//                 String string=word.substring(i,j);
//                 //System.out.println(string);
//                 if(check(string))sum++;
//             }
//         }
//         return sum;
//     }
//     public boolean check(String string) {
//         HashMap<Character, Integer>map=new HashMap<Character, Integer>();
//         char[]c=string.toCharArray();
//         for(int i=0;i<c.length;i++) {
//             map.put(c[i], map.getOrDefault(c[i],0)+1);
//         }
//         int count=0;
//         for(Integer t:map.values()) {
//             if(t%2==1)count++;
//         }
//         return count>1?false:true;
//     }
// }
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-wonderful-substrings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-wonderful-substrings/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-wonderful-substrings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-wonderful-substrings/)

[回到目录](../README.md)