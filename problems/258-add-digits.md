# 258. add-digits | 各位相加

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>num</code>, repeatedly add all its digits until the result has only one digit, and return it.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 38
<strong>Output:</strong> 2
<strong>Explanation:</strong> The process is
38 --&gt; 3 + 8 --&gt; 11
11 --&gt; 1 + 1 --&gt; 2 
Since 2 has only one digit, return it.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= num &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you do it without any loop/recursion in <code>O(1)</code> runtime?</p>
 instead-->
<p>给定一个非负整数 <code>num</code>，反复将各个位上的数字相加，直到结果为一位数。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>38</code>
<strong>输出:</strong> 2 
<strong>解释: </strong>各位相加的过程为<strong>：</strong><code>3 + 8 = 11</code>, <code>1 + 1 = 2</code>。 由于&nbsp;<code>2</code> 是一位数，所以返回 2。
</pre>

<p><strong>进阶:</strong><br>
你可以不使用循环或者递归，且在 O(1) 时间复杂度内解决这个问题吗？</p>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
     public static int addDigits(int num) {
         int sum=0;
         boolean flag=true;
         while(sum/10!=0||flag==true) {
             if(!flag)
             num=sum;
             flag=false;
             sum=0;
             while(num!=0) {
//                 System.out.println("num:"+num);
                 sum+=(num%10);
                 num/=10;
                 
             }
//             System.out.println("sum:"+sum);
         }
            return sum;
        }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-digits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-digits/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-digits/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-digits/)

[回到目录](../README.md)