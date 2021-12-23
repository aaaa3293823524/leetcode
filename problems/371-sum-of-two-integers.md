# 371. sum-of-two-integers | 两整数之和

## Question description

<!--If you want to use the English description, use <p>Given two integers <code>a</code> and <code>b</code>, return <em>the sum of the two integers without using the operators</em> <code>+</code> <em>and</em> <code>-</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> a = 1, b = 2
<strong>Output:</strong> 3
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> a = 2, b = 3
<strong>Output:</strong> 5
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-1000 &lt;= a, b &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你两个整数 <code>a</code> 和 <code>b</code> ，<strong>不使用 </strong>运算符&nbsp;<code>+</code> 和&nbsp;<code>-</code>&nbsp;​​​​​​​，计算并返回两整数之和。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>a = 1, b = 2
<strong>输出：</strong>3
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>a = 2, b = 3
<strong>输出：</strong>5
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>-1000 &lt;= a, b &lt;= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
 public class Solution {
    public int getSum(int a, int b) {
        int and = a & b; //与运算结果，1的位代表两个数值都为1，存在进位
        int eor = a ^ b; //异或运算结果，1的位代表两个数值对应位有一个为1

        //若and不为0，意味着存在进位情况，将进位左移
        if(and != 0) {
            and = and << 1;
        }

        //当进位为1的位数和有一位为1的位数相遇，与运算为1，证明再次存在进位运算
        while((and & eor) != 0){
            //计算新的进位
            int newAnd = and & eor;
            //再次比较出有一位为1的位数
            eor = and ^ eor;
            //把进位左移
            and = newAnd <<1;
        }
        //进位和有一位为1的位已经没有重叠，通过异或运算得出最终位数状态
        //为什么用抑或而不是或运算，因为之前应该进位的位没有改为0，
        //而该进的位已经写到最终的位置，因此原有两位都是1的值要通过抑或变为0
        return and ^ eor;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-two-integers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-two-integers/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-two-integers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-two-integers/)

[回到目录](../README.md)