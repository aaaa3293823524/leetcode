# 剑指 Offer II 032. dKk3P7 | 有效的变位词

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定两个字符串 <code>s</code> 和 <code>t</code> ，编写一个函数来判断它们是不是一组变位词（字母异位词）。</p>

<p><strong>注意：</strong>若&nbsp;<code><em>s</em></code> 和 <code><em>t</em></code><em>&nbsp;</em>中每个字符出现的次数都相同且<strong>字符顺序不完全相同</strong>，则称&nbsp;<code><em>s</em></code> 和 <code><em>t</em></code><em>&nbsp;</em>互为变位词（字母异位词）。</p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong> s = &quot;anagram&quot;, t = &quot;nagaram&quot;
<strong>输出:</strong> true
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> s = &quot;rat&quot;, t = &quot;car&quot;
<strong>输出: </strong>false</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> s = &quot;a&quot;, t = &quot;a&quot;
<strong>输出: </strong>false</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= s.length, t.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code>&nbsp;and&nbsp;<code>t</code>&nbsp;仅包含小写字母</li>
</ul>

<p>&nbsp;</p>

<p><strong>进阶:&nbsp;</strong>如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？</p>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 242&nbsp;题相似（字母异位词定义不同）：<a href="https://leetcode-cn.com/problems/valid-anagram/">https://leetcode-cn.com/problems/valid-anagram/</a></p>




## Solution

Language: **java**  /  Runtime: 31 ms

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s==null^t==null)return false;
        if(s==null||t==null)return true;
        int len1=s.length();
        int len2=t.length();
        if(len1!=len2)return false;
        if(s.equals(t))return false;
        HashMap<Character,Integer>map=new HashMap<Character,Integer>();
        for(int i=0;i<len1;i++){
            map.put(s.charAt(i),map.getOrDefault(s.charAt(i),0)+1);
            map.put(t.charAt(i),map.getOrDefault(t.charAt(i),0)-1);
        }
        
        for(Character g:map.keySet()){
            System.out.println(g+":"+map.get(g));
            if(map.get(g)!=0)return false;
        }
        return true;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/dKk3P7/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/dKk3P7/description/)

Solution: [LeetCode](https://leetcode.com/articles/dKk3P7/)  /  [LeetCode中国](https://leetcode-cn.com/articles/dKk3P7/)

[回到目录](../README.md)