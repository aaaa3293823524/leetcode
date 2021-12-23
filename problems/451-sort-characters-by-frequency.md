# 451. sort-characters-by-frequency | 根据字符出现频率排序

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, sort it in <strong>decreasing order</strong> based on the <strong>frequency</strong> of the characters. The <strong>frequency</strong> of a character is the number of times it appears in the string.</p>

<p>Return <em>the sorted string</em>. If there are multiple answers, return <em>any of them</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;tree&quot;
<strong>Output:</strong> &quot;eert&quot;
<strong>Explanation:</strong> &#39;e&#39; appears twice while &#39;r&#39; and &#39;t&#39; both appear once.
So &#39;e&#39; must appear before both &#39;r&#39; and &#39;t&#39;. Therefore &quot;eetr&quot; is also a valid answer.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;cccaaa&quot;
<strong>Output:</strong> &quot;aaaccc&quot;
<strong>Explanation:</strong> Both &#39;c&#39; and &#39;a&#39; appear three times, so both &quot;cccaaa&quot; and &quot;aaaccc&quot; are valid answers.
Note that &quot;cacaca&quot; is incorrect, as the same characters must be together.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Aabb&quot;
<strong>Output:</strong> &quot;bbAa&quot;
<strong>Explanation:</strong> &quot;bbaA&quot; is also a valid answer, but &quot;Aabb&quot; is incorrect.
Note that &#39;A&#39; and &#39;a&#39; are treated as two different characters.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>s</code> consists of uppercase and lowercase English letters and digits.</li>
</ul>
 instead-->
<p>给定一个字符串，请将字符串里的字符按照出现的频率降序排列。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong>
&quot;tree&quot;

<strong>输出:</strong>
&quot;eert&quot;

<strong>解释:
</strong>&#39;e&#39;出现两次，&#39;r&#39;和&#39;t&#39;都只出现一次。
因此&#39;e&#39;必须出现在&#39;r&#39;和&#39;t&#39;之前。此外，&quot;eetr&quot;也是一个有效的答案。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong>
&quot;cccaaa&quot;

<strong>输出:</strong>
&quot;cccaaa&quot;

<strong>解释:
</strong>&#39;c&#39;和&#39;a&#39;都出现三次。此外，&quot;aaaccc&quot;也是有效的答案。
注意&quot;cacaca&quot;是不正确的，因为相同的字母必须放在一起。
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong>
&quot;Aabb&quot;

<strong>输出:</strong>
&quot;bbAa&quot;

<strong>解释:
</strong>此外，&quot;bbaA&quot;也是一个有效的答案，但&quot;Aabb&quot;是不正确的。
注意&#39;A&#39;和&#39;a&#39;被认为是两种不同的字符。
</pre>




## Solution

Language: **java**  /  Runtime: 348 ms

```java
class Solution {
    public static String frequencySort(String s) {
//        设置返回的字符串
        String str="";
//        1. 通过哈希统计词频 2. 将value存入优先队列中进行排序 3. 最后遍历输出
        
        Map<Character, Integer> map=new HashMap<Character, Integer>();
        for(int i=0;i<s.length();i++) {
            System.out.println(s.charAt(i));
            map.put(s.charAt(i),map.getOrDefault(s.charAt(i), 0)+1);
        }
        System.out.println(map);//{r=1, t=1, e=2}
//        设置优先队列，由于题目要求降序，所以使用大顶堆
        PriorityQueue<str> queue=new PriorityQueue<>(new Comparator<str>() {
            public int compare(str o1,str o2) {
                return o2.getCount()-o1.getCount();//大顶堆
            }
        });
//        通过for循环将对应的值入队
        for(Map.Entry<Character, Integer> entry : map.entrySet()) {
            queue.offer(new str(entry.getKey(),entry.getValue()));
        }
        while(!queue.isEmpty()) {
            str+=queue.poll();
            System.out.println(str);
        }

        return str;
    }
//创建一个数据类Data，包含一个char类型的字符和int类型的次数
    public static class str{
        char c;
        int  num;
//        构造函数
        public str(char c ,int num) {
            // TODO 自动生成的构造函数存根
            this.c=c;
            this.num=num;
        }
        public char getC() {
            return this.c;
        }
        public int getCount() {
            return this.num;
        }
//        返回字符串
        public String toString() {
//            String str="";
            StringBuilder str = new StringBuilder();
            for (int i=0;i<num;i++) {
                str.append(c);
            }
            return str.toString();
        }
    }

}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sort-characters-by-frequency/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sort-characters-by-frequency/description/)

Solution: [LeetCode](https://leetcode.com/articles/sort-characters-by-frequency/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sort-characters-by-frequency/)

[回到目录](../README.md)