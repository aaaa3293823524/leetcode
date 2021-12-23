# 791. custom-sort-string | 自定义字符串排序

## Question description

<!--If you want to use the English description, use <p>You are given two strings order and s. All the words of <code>order</code> are <strong>unique</strong> and were sorted in some custom order previously.</p>

<p>Permute the characters of <code>s</code> so that they match the order that <code>order</code> was sorted. More specifically, if a character <code>x</code> occurs before a character <code>y</code> in <code>order</code>, then <code>x</code> should occur before <code>y</code> in the permuted string.</p>

<p>Return <em>any permutation of </em><code>s</code><em> that satisfies this property</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> order = &quot;cba&quot;, s = &quot;abcd&quot;
<strong>Output:</strong> &quot;cbad&quot;
<strong>Explanation:</strong> 
&quot;a&quot;, &quot;b&quot;, &quot;c&quot; appear in order, so the order of &quot;a&quot;, &quot;b&quot;, &quot;c&quot; should be &quot;c&quot;, &quot;b&quot;, and &quot;a&quot;. 
Since &quot;d&quot; does not appear in order, it can be at any position in the returned string. &quot;dcba&quot;, &quot;cdba&quot;, &quot;cbda&quot; are also valid outputs.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> order = &quot;cbafg&quot;, s = &quot;abcd&quot;
<strong>Output:</strong> &quot;cbad&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= order.length &lt;= 26</code></li>
	<li><code>1 &lt;= s.length &lt;= 200</code></li>
	<li><code>order</code> and <code>s</code> consist of lowercase English letters.</li>
	<li>All the characters of <code>order</code> are <strong>unique</strong>.</li>
</ul>
 instead-->
<p>字符串<code>S</code>和 <code>T</code> 只包含小写字符。在<code>S</code>中，所有字符只会出现一次。</p>

<p><code>S</code> 已经根据某种规则进行了排序。我们要根据<code>S</code>中的字符顺序对<code>T</code>进行排序。更具体地说，如果<code>S</code>中<code>x</code>在<code>y</code>之前出现，那么返回的字符串中<code>x</code>也应出现在<code>y</code>之前。</p>

<p>返回任意一种符合条件的字符串<code>T</code>。</p>

<pre>
<strong>示例:</strong>
<strong>输入:</strong>
S = &quot;cba&quot;
T = &quot;abcd&quot;
<strong>输出:</strong> &quot;cbad&quot;
<strong>解释:</strong> 
S中出现了字符 &quot;a&quot;, &quot;b&quot;, &quot;c&quot;, 所以 &quot;a&quot;, &quot;b&quot;, &quot;c&quot; 的顺序应该是 &quot;c&quot;, &quot;b&quot;, &quot;a&quot;. 
由于 &quot;d&quot; 没有在S中出现, 它可以放在T的任意位置. &quot;dcba&quot;, &quot;cdba&quot;, &quot;cbda&quot; 都是合法的输出。
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>S</code>的最大长度为<code>26</code>，其中没有重复的字符。</li>
	<li><code>T</code>的最大长度为<code>200</code>。</li>
	<li><code>S</code>和<code>T</code>只包含小写字符。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public String customSortString(String order, String s) {
         HashMap<Character, Integer>map=new HashMap<Character, Integer>();
         char[]c=order.toCharArray();
         
         //int index[]=new int[c.length];
         for(int i=0;i<c.length;i++) {
             map.put(c[i], i);
             //index[]=
         }
         char[]string=s.toCharArray();
         List<Character>list=new ArrayList<Character>();
         for(int i=0;i<string.length;i++) {
             list.add(string[i]);
         }
        //  for(char gg:map.keySet()){
        //     System.out.println(gg+" "+map.get(gg));
        //  }
         Collections.sort(list,new Comparator<Character>() {

            @Override
            public int compare(Character o1, Character o2) {
                // TODO Auto-generated method stub
                //if(!map.containsKey(o1)||!map.containsKey(o2))return 0;
                return map.getOrDefault(o1,0)-map.getOrDefault(o2,0);
            }
             
        });
         StringBuilder stringBuilder=new StringBuilder();
         for(int i=0;i<string.length;i++) {
             stringBuilder.append(list.get(i));
         }
        return stringBuilder.toString();
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/custom-sort-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/custom-sort-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/custom-sort-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/custom-sort-string/)

[回到目录](../README.md)