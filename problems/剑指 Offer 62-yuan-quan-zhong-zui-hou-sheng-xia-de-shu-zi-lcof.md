# 剑指 Offer 62. yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof | 圆圈中最后剩下的数字

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>0,1,···,n-1这n个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数字（删除后从下一个数字开始计数）。求出这个圆圈里剩下的最后一个数字。</p>

<p>例如，0、1、2、3、4这5个数字组成一个圆圈，从数字0开始每次删除第3个数字，则删除的前4个数字依次是2、0、4、1，因此最后剩下的数字是3。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入:</strong> n = 5, m = 3
<strong>输出: </strong>3
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入:</strong> n = 10, m = 17
<strong>输出: </strong>2
</pre>

<p> </p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>1 <= n <= 10^5</code></li>
	<li><code>1 <= m <= 10^6</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1362 ms

```java
class Solution {
    public int lastRemaining(int n, int m) {
        List<Integer>list=new ArrayList<Integer>();
        for(int i=0;i<n;i++){
            list.add(i);
        }
        int cur=0;
        while(list.size()!=1){
            cur=(cur+m-1)%(list.size());
            list.remove(cur);
        }
        return list.get(0);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/)

[回到目录](../README.md)