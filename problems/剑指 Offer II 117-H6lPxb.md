# 剑指 Offer II 117. H6lPxb | 相似的字符串

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>如果交换字符串&nbsp;<code>X</code> 中的两个不同位置的字母，使得它和字符串&nbsp;<code>Y</code> 相等，那么称 <code>X</code> 和 <code>Y</code> 两个字符串相似。如果这两个字符串本身是相等的，那它们也是相似的。</p>

<p>例如，<code>&quot;tars&quot;</code> 和 <code>&quot;rats&quot;</code> 是相似的 (交换 <code>0</code> 与 <code>2</code> 的位置)；&nbsp;<code>&quot;rats&quot;</code> 和 <code>&quot;arts&quot;</code> 也是相似的，但是 <code>&quot;star&quot;</code> 不与 <code>&quot;tars&quot;</code>，<code>&quot;rats&quot;</code>，或 <code>&quot;arts&quot;</code> 相似。</p>

<p>总之，它们通过相似性形成了两个关联组：<code>{&quot;tars&quot;, &quot;rats&quot;, &quot;arts&quot;}</code> 和 <code>{&quot;star&quot;}</code>。注意，<code>&quot;tars&quot;</code> 和 <code>&quot;arts&quot;</code> 是在同一组中，即使它们并不相似。形式上，对每个组而言，要确定一个单词在组中，只需要这个词和该组中至少一个单词相似。</p>

<p>给定一个字符串列表 <code>strs</code>。列表中的每个字符串都是 <code>strs</code> 中其它所有字符串的一个&nbsp;<strong>字母异位词&nbsp;</strong>。请问 <code>strs</code> 中有多少个相似字符串组？</p>

<p><strong>字母异位词（anagram）</strong>，一种把某个字符串的字母的位置（顺序）加以改换所形成的新词。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>strs = [&quot;tars&quot;,&quot;rats&quot;,&quot;arts&quot;,&quot;star&quot;]
<strong>输出：</strong>2
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>strs = [&quot;omv&quot;,&quot;ovm&quot;]
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 300</code></li>
	<li><code>1 &lt;= strs[i].length &lt;= 300</code></li>
	<li><code>strs[i]</code> 只包含小写字母。</li>
	<li><code>strs</code> 中的所有单词都具有相同的长度，且是彼此的字母异位词。</li>
</ul>

<p>&nbsp; &nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 839&nbsp;题相同：<a href="https://leetcode-cn.com/problems/similar-string-groups/">https://leetcode-cn.com/problems/similar-string-groups/</a></p>




## Solution

Language: **java**  /  Runtime: 121 ms

```java
class Solution {
    public int numSimilarGroups(String[] strs) {
        int n = strs.length;
        int cnt = n;
        int[] fathers = new int[n];
        for(int i = 0; i < n; ++i){
            fathers[i] = i;
        }
        for(int i = 0; i < n; ++i){
            for(int j = i+1; j < n; ++j){
                if(isSimilar(strs[i], strs[j]) && union(fathers, i, j)){
                    cnt--;
                }
            }
        }
        return cnt;
    }

    public boolean isSimilar(String s1, String s2){
        int cnt = 0;
        for(int i = 0; i < s1.length(); ++i){
            if(s1.charAt(i) != s2.charAt(i)) cnt++;
        }
        return cnt<=2;
    }

    public boolean union(int[] fathers, int i, int j){
        int a = findFather(fathers, i);
        int b = findFather(fathers, j);
        if(a != b){
            fathers[a] = b;
            return true;
        }
        return false;
    }

    public int findFather(int[] fathers, int i){
        if(fathers[i] != i){
            fathers[i] = findFather(fathers, fathers[i]);
        }
        return fathers[i];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/H6lPxb/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/H6lPxb/description/)

Solution: [LeetCode](https://leetcode.com/articles/H6lPxb/)  /  [LeetCode中国](https://leetcode-cn.com/articles/H6lPxb/)

[回到目录](../README.md)