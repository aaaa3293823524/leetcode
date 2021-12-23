# 剑指 Offer 50. di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof | 第一个只出现一次的字符

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。</p>

<p><strong>示例 1:</strong></p>

<pre>
输入：s = "abaccdeff"
输出：'b'
</pre>

<p><strong>示例 2:</strong></p>

<pre>
输入：s = "" 
输出：' '
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= s 的长度 &lt;= 50000</code></p>


## Note

有序哈希表


## Solution

Language: **java**  /  Runtime: 29 ms

```java
class Solution {
    public char firstUniqChar(String s) {
        Map<Character, Boolean> dic = new LinkedHashMap<>();
        char[] sc = s.toCharArray();
        for(char c : sc)
            dic.put(c, !dic.containsKey(c));
        System.out.println(dic);
        for(Map.Entry<Character, Boolean> d : dic.entrySet()){
           if(d.getValue()) return d.getKey();
        }
        return ' ';
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

[回到目录](../README.md)