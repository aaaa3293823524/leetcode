# 剑指 Offer 66. gou-jian-cheng-ji-shu-zu-lcof | 构建乘积数组

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>给定一个数组 <code>A[0,1,…,n-1]</code>，请构建一个数组 <code>B[0,1,…,n-1]</code>，其中 <code>B[i]</code> 的值是数组 <code>A</code> 中除了下标 <code>i</code> 以外的元素的积, 即 <code>B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]</code>。不能使用除法。</p>

<p> </p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3,4,5]
<strong>输出:</strong> [120,60,40,30,24]</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>所有元素乘积之和不会溢出 32 位整数</li>
	<li><code>a.length <= 100000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int[] constructArr(int[] a) {
        int len = a.length;
        if(len == 0) return new int[0];
        int[] b = new int[len];
        b[0] = 1;
        int tmp = 1;
        for(int i = 1; i < len; i++) {
            b[i] = b[i - 1] * a[i - 1];
        }
        for(int i = len - 2; i >= 0; i--) {
            tmp *= a[i + 1];
            b[i] *= tmp;
        }
        return b;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/gou-jian-cheng-ji-shu-zu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/gou-jian-cheng-ji-shu-zu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/gou-jian-cheng-ji-shu-zu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/gou-jian-cheng-ji-shu-zu-lcof/)

[回到目录](../README.md)