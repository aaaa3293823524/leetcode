# 剑指 Offer 05. ti-huan-kong-ge-lcof | 替换空格

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>请实现一个函数，把字符串 <code>s</code> 中的每个空格替换成&quot;%20&quot;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;We are happy.&quot;
<strong>输出：</strong>&quot;We%20are%20happy.&quot;</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= s 的长度 &lt;= 10000</code></p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public String replaceSpace(String s) {
        int length = s.length();
        char[] array = new char[length * 3];
        int size = 0;
        for (int i = 0; i < length; i++) {
            char c = s.charAt(i);
            if (c == ' ') {
                array[size++] = '%';
                array[size++] = '2';
                array[size++] = '0';
            } else {
                array[size++] = c;
            }
        }
        String newStr = new String(array, 0, size);
        return newStr;
    }
}


```

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def replaceSpace(self, s: str) -> str:
        return s.replace(' ','%20')
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ti-huan-kong-ge-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/ti-huan-kong-ge-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ti-huan-kong-ge-lcof/)

[回到目录](../README.md)