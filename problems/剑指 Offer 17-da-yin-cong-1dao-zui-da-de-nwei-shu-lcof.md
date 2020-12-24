# 剑指 Offer 17. da-yin-cong-1dao-zui-da-de-nwei-shu-lcof | 打印从1到最大的n位数

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>输入数字 <code>n</code>，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> n = 1
<strong>输出:</strong> [1,2,3,4,5,6,7,8,9]
</pre>

<p>&nbsp;</p>

<p>说明：</p>

<ul>
	<li>用返回一个整数列表来代替打印</li>
	<li>n 为正整数</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int[] printNumbers(int n) {
        int end = (int)Math.pow(10, n) - 1;
        int[] res = new int[end];
        for(int i = 0; i < end; i++)
            res[i] = i + 1;
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)

[回到目录](../README.md)