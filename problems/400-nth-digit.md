# 400. nth-digit | 第 N 位数字

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>n</code>, return the <code>n<sup>th</sup></code> digit of the infinite integer sequence <code>[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3
<strong>Output:</strong> 3
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 11
<strong>Output:</strong> 0
<strong>Explanation:</strong> The 11<sup>th</sup> digit of the sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... is a 0, which is part of the number 10.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给你一个整数 <code>n</code> ，请你在无限的整数序列&nbsp;<code>[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...]</code> 中找出并返回第&nbsp;<code>n</code><em> </em>位上的数字。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>3
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 11
<strong>输出：</strong>0
<strong>解释：</strong>第 11 位数字在序列 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... 里是 <strong>0 </strong>，它是 10 的一部分。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
	<li>第 <code>n</code> 位上的数字是按计数单位（digit）从前往后数的第 <code>n</code> 个数，参见 <strong>示例 2</strong> 。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    private static int[] table1 = new int[10];// table1[2] 表示2位数上一共多少个数(按位算)
    private static int[] table2 = new int[10];// table2[2] 表示2位数之前一共多少个数

    static {
        for (int i = 1; i < 9; i++) {
            table1[i] = ((int) Math.pow(10, i) - (int) Math.pow(10, i - 1)) * i;
        }
        table2[9] = Integer.MAX_VALUE;

        for (int i = 1; i < 9; i++) {
            table2[i] += table2[i - 1] + table1[i];
        }

    }

    public int findNthDigit(int n) {
        int w = 0;// n是w+1位数, w是n的位数-1
        for (; w < 9; w++) {
            if (n <= table2[w + 1]) {
                break;
            }
        }
        int left = n - table2[w];// n的前一位所有数字都减掉
        int num = left / (w + 1) + (int) Math.pow(10, w);// n是哪个数上的一位
        int mod = left % (w + 1); // n是num第几个
        if (mod == 0) {
            num = num - 1;// 余0是上一个数的最后一位
            return num - (num / 10) * 10;
        } else {
            num = num / (int) Math.pow(10, w + 1 - mod);// 将num的第mod个数变成个位数
            return num - (num / 10) * 10;// 取出个位数
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/nth-digit/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/nth-digit/description/)

Solution: [LeetCode](https://leetcode.com/articles/nth-digit/)  /  [LeetCode中国](https://leetcode-cn.com/articles/nth-digit/)

[回到目录](../README.md)