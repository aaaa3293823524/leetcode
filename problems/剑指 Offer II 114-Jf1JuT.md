# 剑指 Offer II 114. Jf1JuT | 外星文字典

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>现有一种使用英语字母的外星文语言，这门语言的字母顺序与英语顺序不同。</p>

<p>给定一个字符串列表 <code>words</code> ，作为这门语言的词典，<code>words</code> 中的字符串已经 <strong>按这门新语言的字母顺序进行了排序</strong> 。</p>

<p>请你根据该词典还原出此语言中已知的字母顺序，并 <strong>按字母递增顺序</strong> 排列。若不存在合法字母顺序，返回 <code>&quot;&quot;</code> 。若存在多种可能的合法字母顺序，返回其中 <strong>任意一种</strong> 顺序即可。</p>

<p>字符串 <code>s</code> <strong>字典顺序小于</strong> 字符串 <code>t</code> 有两种情况：</p>

<ul>
	<li>在第一个不同字母处，如果 <code>s</code> 中的字母在这门外星语言的字母顺序中位于 <code>t</code> 中字母之前，那么&nbsp;<code>s</code> 的字典顺序小于 <code>t</code> 。</li>
	<li>如果前面 <code>min(s.length, t.length)</code> 字母都相同，那么 <code>s.length &lt; t.length</code> 时，<code>s</code> 的字典顺序也小于 <code>t</code> 。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>words = [&quot;wrt&quot;,&quot;wrf&quot;,&quot;er&quot;,&quot;ett&quot;,&quot;rftt&quot;]
<strong>输出：</strong>&quot;wertf&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>words = [&quot;z&quot;,&quot;x&quot;]
<strong>输出：</strong>&quot;zx&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>words = [&quot;z&quot;,&quot;x&quot;,&quot;z&quot;]
<strong>输出：</strong>&quot;&quot;
<strong>解释：</strong>不存在合法字母顺序，因此返回 <code>&quot;&quot; 。</code>
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 100</code></li>
	<li><code>words[i]</code> 仅由小写英文字母组成</li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 269&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/alien-dictionary/">https://leetcode-cn.com/problems/alien-dictionary/</a></p>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public String alienOrder(String[] words) {
        Map<Character, Set<Character>> graph = new HashMap<>();
        int[] inDegree = new int[26];
        Queue<Character> q = new LinkedList<>();
        StringBuilder sb = new StringBuilder();
        //把出现的字符保存在图HashMap里，每个不重复字符对应一个表示有序的有向边
        for(String word : words){
            for(char ch : word.toCharArray()){
                graph.putIfAbsent(ch, new HashSet<>());
            }
        }
        //两两比较相邻字符串之间的关系
        for(int i = 1; i < words.length; ++i){
            String w1 = words[i-1];
            String w2 = words[i];
            if(checkPre(w1,w2) && !w1.equals(w2)) return ""; //检查为不合法输入
            for(int j = 0; j < Math.min(w1.length(), w2.length()); ++j){
                char c1 = w1.charAt(j);
                char c2 = w2.charAt(j);
                //找到不同的字符才说明有顺序关系，把前一个字符指向后一字符，同时后一字符的入度+1
                if(c1 != c2){
                    if(!graph.get(c1).contains(c2)){
                        graph.get(c1).add(c2);
                        inDegree[c2 - 'a']++;
                    }
                    break;
                }
            }
        }
        //把所有入度为0的字符先加入队列，准备拓扑排序
        for(char ch : graph.keySet()){
            if(inDegree[ch - 'a'] == 0) q.offer(ch);
        }
        while(!q.isEmpty()){
            char node = q.poll();
            //从队列出来的这个字符肯定是入度为0，可以确定它的顺序，就把它加进字符顺序的结果里
            sb.append(node);
            //取出当前出来的节点以后，该节点所有的出度(有向边指向所有节点的节点入度)都要减1，若有入度为0的节点字符出现，把它加进队列准备之后的拓扑排序遍历
            for(char next : graph.get(node)){
                inDegree[next - 'a']--;
                if(inDegree[next - 'a'] == 0) q.offer(next);
            }
        }
        //如果结果集里的字符数量和图中所有节点数量相同，说明拓扑排序成功，返回结果集，否则不成功，不存在合法字母顺序
        return sb.length() == graph.size() ? sb.toString() : "";
    }

    public boolean checkPre(String s1, String s2){
        int m = s1.length(), n = s2.length();
        if(m < n) return false;
        int i = 0, j = 0;
        while(i < m && j < n){
            if(s2.charAt(j) != s1.charAt(i)) return false;
            i++;
            j++;
        }
        return true;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/Jf1JuT/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/Jf1JuT/description/)

Solution: [LeetCode](https://leetcode.com/articles/Jf1JuT/)  /  [LeetCode中国](https://leetcode-cn.com/articles/Jf1JuT/)

[回到目录](../README.md)