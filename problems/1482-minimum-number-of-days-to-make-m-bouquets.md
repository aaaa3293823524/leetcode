# 1482. minimum-number-of-days-to-make-m-bouquets | 制作 m 束花所需的最少天数

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>bloomDay</code>, an integer <code>m</code> and an integer <code>k</code>.</p>

<p>You want to make <code>m</code> bouquets. To make a bouquet, you need to use <code>k</code> <strong>adjacent flowers</strong> from the garden.</p>

<p>The garden consists of <code>n</code> flowers, the <code>i<sup>th</sup></code> flower will bloom in the <code>bloomDay[i]</code> and then can be used in <strong>exactly one</strong> bouquet.</p>

<p>Return <em>the minimum number of days you need to wait to be able to make </em><code>m</code><em> bouquets from the garden</em>. If it is impossible to make m bouquets return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> bloomDay = [1,10,3,10,2], m = 3, k = 1
<strong>Output:</strong> 3
<strong>Explanation:</strong> Let us see what happened in the first three days. x means flower bloomed and _ means flower did not bloom in the garden.
We need 3 bouquets each should contain 1 flower.
After day 1: [x, _, _, _, _]   // we can only make one bouquet.
After day 2: [x, _, _, _, x]   // we can only make two bouquets.
After day 3: [x, _, x, _, x]   // we can make 3 bouquets. The answer is 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> bloomDay = [1,10,3,10,2], m = 3, k = 2
<strong>Output:</strong> -1
<strong>Explanation:</strong> We need 3 bouquets each has 2 flowers, that means we need 6 flowers. We only have 5 flowers so it is impossible to get the needed bouquets and we return -1.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> bloomDay = [7,7,7,7,12,7,7], m = 2, k = 3
<strong>Output:</strong> 12
<strong>Explanation:</strong> We need 2 bouquets each should have 3 flowers.
Here is the garden after the 7 and 12 days:
After day 7: [x, x, x, x, _, x, x]
We can make one bouquet of the first three flowers that bloomed. We cannot make another bouquet from the last three flowers that bloomed because they are not adjacent.
After day 12: [x, x, x, x, x, x, x]
It is obvious that we can make two bouquets in different ways.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>bloomDay.length == n</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= bloomDay[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= m &lt;= 10<sup>6</sup></code></li>
	<li><code>1 &lt;= k &lt;= n</code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>bloomDay</code>，以及两个整数 <code>m</code> 和 <code>k</code> 。</p>

<p>现需要制作 <code>m</code> 束花。制作花束时，需要使用花园中 <strong>相邻的 <code>k</code> 朵花</strong> 。</p>

<p>花园中有 <code>n</code> 朵花，第 <code>i</code> 朵花会在 <code>bloomDay[i]</code> 时盛开，<strong>恰好</strong> 可以用于 <strong>一束</strong> 花中。</p>

<p>请你返回从花园中摘 <code>m</code> 束花需要等待的最少的天数。如果不能摘到 <code>m</code> 束花则返回 <strong>-1</strong> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>bloomDay = [1,10,3,10,2], m = 3, k = 1
<strong>输出：</strong>3
<strong>解释：</strong>让我们一起观察这三天的花开过程，x 表示花开，而 _ 表示花还未开。
现在需要制作 3 束花，每束只需要 1 朵。
1 天后：[x, _, _, _, _]   // 只能制作 1 束花
2 天后：[x, _, _, _, x]   // 只能制作 2 束花
3 天后：[x, _, x, _, x]   // 可以制作 3 束花，答案为 3
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>bloomDay = [1,10,3,10,2], m = 3, k = 2
<strong>输出：</strong>-1
<strong>解释：</strong>要制作 3 束花，每束需要 2 朵花，也就是一共需要 6 朵花。而花园中只有 5 朵花，无法满足制作要求，返回 -1 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>bloomDay = [7,7,7,7,12,7,7], m = 2, k = 3
<strong>输出：</strong>12
<strong>解释：</strong>要制作 2 束花，每束需要 3 朵。
花园在 7 天后和 12 天后的情况如下：
7 天后：[x, x, x, x, _, x, x]
可以用前 3 朵盛开的花制作第一束花。但不能使用后 3 朵盛开的花，因为它们不相邻。
12 天后：[x, x, x, x, x, x, x]
显然，我们可以用不同的方式制作两束花。
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>bloomDay = [1000000000,1000000000], m = 1, k = 1
<strong>输出：</strong>1000000000
<strong>解释：</strong>需要等 1000000000 天才能采到花来制作花束
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：</strong>bloomDay = [1,10,2,9,3,8,4,7,5,6], m = 4, k = 2
<strong>输出：</strong>9
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>bloomDay.length == n</code></li>
	<li><code>1 &lt;= n &lt;= 10^5</code></li>
	<li><code>1 &lt;= bloomDay[i] &lt;= 10^9</code></li>
	<li><code>1 &lt;= m &lt;= 10^6</code></li>
	<li><code>1 &lt;= k &lt;= n</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 24 ms

```java
class Solution {
    public int minDays(int[] bloomDay, int m, int k) {

        if( m > bloomDay.length / k) return -1; // 此时无论如何都制作不出来m束花

        // 只要 m <= bloomDay.length / k, 成立，无论如何都能制作出来
        // 调用两次stream()方法求最值的效率较低，可以使用常规方法替代！
        int low = Arrays.stream(bloomDay).min().getAsInt(); // 花开的最小天数
        int high = Arrays.stream(bloomDay).max().getAsInt(); // 花开的最大天数

        // 如果可以制作m束花，天数一定在low和high之间，因此使用二分查找
        while(low < high){
            int mid = low + (high-low)/2;
            if(make(bloomDay,m,k,mid)){
                high = mid;
            }else low = mid+1;
        }
        return low;
        
    }

    public boolean make(int[] bloomDay, int m, int k,int days){
        int flowers = 0; // 代表可用的花的个数
        int makeFlowers = 0; // 代表当前天数days可以制作出的花的数量
        int n = bloomDay.length;
        for(int i = 0; i < n; i++){
            if(bloomDay[i] <= days){
                flowers++; // 只要开花所需天数小于等于days, 则说明当前花可用
                if(flowers == k){   // 当前花的数量满足可以制作一束花的数量k时，则制作出的花的数量makeFlowers++;并重置makeFlowers
                    makeFlowers++;
                    flowers = 0;  // 重置当前可用花的数量
                }
            }else flowers = 0; // 因为需要连续的k朵花，因此只要中间有一朵花没开, flowers就重置为0   
            
        }
        return makeFlowers >= m; // 只要 makeFlowers >= m 就说明可以满足要求
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-number-of-days-to-make-m-bouquets/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-number-of-days-to-make-m-bouquets/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-number-of-days-to-make-m-bouquets/)

[回到目录](../README.md)