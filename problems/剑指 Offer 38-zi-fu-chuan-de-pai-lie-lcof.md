# 剑指 Offer 38. zi-fu-chuan-de-pai-lie-lcof | 字符串的排列

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>输入一个字符串，打印出该字符串中字符的所有排列。</p>

<p>&nbsp;</p>

<p>你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入：</strong>s = &quot;abc&quot;
<strong>输出：[</strong>&quot;abc&quot;,&quot;acb&quot;,&quot;bac&quot;,&quot;bca&quot;,&quot;cab&quot;,&quot;cba&quot;<strong>]</strong>
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>1 &lt;= s 的长度 &lt;= 8</code></p>




## Solution

Language: **java**  /  Runtime: 75 ms

```java
class Solution {
    public static void full(Set<String>set,char[] data,int length) {
        
        if(length==data.length-1) {
            set.add(String.valueOf(data));
            
        }
        for(int i=length;i<data.length;i++) {
            char temp=data[length];data[length]=data[i];data[i]=temp;
            full(set,data,length+1);
            temp=data[length];data[length]=data[i];data[i]=temp;//回溯 
        }
        
    }
    public String[] permutation(String s) {
        char[]c=s.toCharArray();
        Set<String>set=new TreeSet<String>();
        int size=0;
        full(set, c, 0);
        System.out.println(set);
        // System.out.println(size);
        // String[] strings=new String[size+1];
        int i=0;
        for(String string:set) {
            
            size++;
        }
        String[] strings=new String[size];
        for(String string:set) {
            
            strings[i++]=string;
        }
        return strings;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/zi-fu-chuan-de-pai-lie-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/zi-fu-chuan-de-pai-lie-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/zi-fu-chuan-de-pai-lie-lcof/)

[回到目录](../README.md)