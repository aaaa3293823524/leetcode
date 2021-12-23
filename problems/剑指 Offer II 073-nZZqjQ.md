# 剑指 Offer II 073. nZZqjQ | 狒狒吃香蕉

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>狒狒喜欢吃香蕉。这里有&nbsp;<code>N</code>&nbsp;堆香蕉，第 <code>i</code> 堆中有&nbsp;<code>piles[i]</code>&nbsp;根香蕉。警卫已经离开了，将在&nbsp;<code>H</code>&nbsp;小时后回来。</p>

<p>狒狒可以决定她吃香蕉的速度&nbsp;<code>K</code>&nbsp;（单位：根/小时）。每个小时，她将会选择一堆香蕉，从中吃掉 <code>K</code> 根。如果这堆香蕉少于 <code>K</code> 根，她将吃掉这堆的所有香蕉，然后这一小时内不会再吃更多的香蕉，下一个小时才会开始吃另一堆的香蕉。&nbsp;&nbsp;</p>

<p>狒狒喜欢慢慢吃，但仍然想在警卫回来前吃掉所有的香蕉。</p>

<p>返回她可以在 <code>H</code> 小时内吃掉所有香蕉的最小速度 <code>K</code>（<code>K</code> 为整数）。</p>

<p>&nbsp;</p>

<ul>
</ul>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入: </strong>piles = [3,6,7,11], H = 8
<strong>输出: </strong>4
</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre>
<strong>输入: </strong>piles = [30,11,23,4,20], H = 5
<strong>输出: </strong>30
</pre>

<p><strong>示例&nbsp;3：</strong></p>

<pre>
<strong>输入: </strong>piles = [30,11,23,4,20], H = 6
<strong>输出: </strong>23
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= piles.length &lt;= 10^4</code></li>
	<li><code>piles.length &lt;= H &lt;= 10^9</code></li>
	<li><code>1 &lt;= piles[i] &lt;= 10^9</code></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 875&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/koko-eating-bananas/">https://leetcode-cn.com/problems/koko-eating-bananas/</a></p>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {

    private int[] piles;
    public int minEatingSpeed(int[] piles, int h) {
        this.piles = piles;
        // 获取最大速度, 由于一次最多只能吃一堆香蕉, 所以最大速度为最大一堆香蕉的数量
        int maxSpeed = Integer.MIN_VALUE;
        for(int pile : piles){
            maxSpeed = Math.max(maxSpeed, pile);
        }
        // 左指针是最小速度, 右指针是最大速度
        int left = 1, right = maxSpeed;
        while (left < right){
            int mid = left + (right - left) / 2;
            if(getEattingHour(mid) > h){
                // 当以 mid 速度吃完香蕉的时间 > h , 则提速要提升, left 指针右移
                left = mid + 1;
            }else{
                // 当以 mid 速度吃完香蕉的时间 <= h , 则最低吃香蕉速度可能为 mid, 或者 比 mid 小 ,
                // 所以, right = mid , 而不是 mid - 1
                right = mid;
            }
        }
        // 最终 left == right, 指向就是最小速度
        return left;
    }

    // 计算以 speed 的速度吃完香蕉的时间
    private int getEattingHour(int speed){
        int hour = 0;
        // 由于,每次最多吃一堆, 所以吃完香蕉的总时间需要 计算每堆香蕉吃完的时间
        for(int pile : piles){
            // 每堆香蕉吃完的时间 = 这一堆香蕉数/吃的速度, 结果向上取整
            hour += (pile + speed - 1) / speed;
        }
        return hour;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/nZZqjQ/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/nZZqjQ/description/)

Solution: [LeetCode](https://leetcode.com/articles/nZZqjQ/)  /  [LeetCode中国](https://leetcode-cn.com/articles/nZZqjQ/)

[回到目录](../README.md)