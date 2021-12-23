# 剑指 Offer 46. ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof | 把数字翻译成字符串

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 &ldquo;a&rdquo; ，1 翻译成 &ldquo;b&rdquo;，&hellip;&hellip;，11 翻译成 &ldquo;l&rdquo;，&hellip;&hellip;，25 翻译成 &ldquo;z&rdquo;。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 12258
<strong>输出:</strong> <code>5
</code><strong>解释:</strong> 12258有5种不同的翻译，分别是&quot;bccfi&quot;, &quot;bwfi&quot;, &quot;bczi&quot;, &quot;mcfi&quot;和&quot;mzi&quot;</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= num &lt; 2<sup>31</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int translateNum(int num) {
        //将字符串转化为数字
        String str = String.valueOf(num);
        //dfs遍历字符串求解
        return dfs(str, 0);
    }
    //表示从index位置开始有好多种翻译方法
    public int dfs(String str, int index){
        //如果当前的下标大于等于字符串的长度 - 1，则说明当前位置是由上一次跳到此处的，则直接返回1
        if(index >= str.length() - 1)
            return 1;
        //先求解每一次都翻译一个字符的方法数
        int res = dfs(str, index + 1);
        //以当前字符的下标为开始，截取两位，判断这位组成的数字是否在10~25之间
        //如果在这一次就可以直接翻译两个字符，然后从两个字符后面的位置开始翻译
        String temp = str.substring(index, index + 2);
        if(temp.compareTo("10") >= 0 && temp.compareTo("25") <= 0)
            res += dfs(str, index + 2);
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)

[回到目录](../README.md)