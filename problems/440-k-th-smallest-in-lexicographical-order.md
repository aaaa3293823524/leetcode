# 440. k-th-smallest-in-lexicographical-order | 字典序的第K小数字

## Question description

<!--If you want to use the English description, use <p>Given two integers <code>n</code> and <code>k</code>, return <em>the</em> <code>k<sup>th</sup></code> <em>lexicographically smallest integer in the range</em> <code>[1, n]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 13, k = 2
<strong>Output:</strong> 10
<strong>Explanation:</strong> The lexicographical order is [1, 10, 11, 12, 13, 2, 3, 4, 5, 6, 7, 8, 9], so the second smallest number is 10.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 1, k = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定整数&nbsp;<code>n</code>&nbsp;和&nbsp;<code>k</code>，找到&nbsp;<code>1</code>&nbsp;到&nbsp;<code>n</code>&nbsp;中字典序第&nbsp;<code>k</code>&nbsp;小的数字。</p>

<p>注意：1 &le; k &le; n &le; 10<sup>9</sup>。</p>

<p><strong>示例 :</strong></p>

<pre>
<strong>输入:</strong>
n: 13   k: 2

<strong>输出:</strong>
10

<strong>解释:</strong>
字典序的排列是 [1, 10, 11, 12, 13, 2, 3, 4, 5, 6, 7, 8, 9]，所以第二小的数字是 10。
</pre>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int findKthNumber(int n, int k) {
        long cur = 1;
        while(k>1){
            long cnt = count(n,cur);
            if(k <= cnt){
                cur*=10;
                k-=1;
            }else{
                cur+=1;
                k-=cnt;
            }
        }
        return (int)cur;
    }

    public long count(int n,long cur){
        long next = cur+1,cnt = 0;
        while(cur<=n){
            cnt += Math.min(n-cur+1,next-cur);
            cur*=10;
            next*=10;
        }
        return cnt;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/k-th-smallest-in-lexicographical-order/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/k-th-smallest-in-lexicographical-order/description/)

Solution: [LeetCode](https://leetcode.com/articles/k-th-smallest-in-lexicographical-order/)  /  [LeetCode中国](https://leetcode-cn.com/articles/k-th-smallest-in-lexicographical-order/)

[回到目录](../README.md)