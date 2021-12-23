# 1691. maximum-height-by-stacking-cuboids | 堆叠长方体的最大高度

## Question description

<!--If you want to use the English description, use <p>Given <code>n</code> <code>cuboids</code> where the dimensions of the <code>i<sup>th</sup></code> cuboid is <code>cuboids[i] = [width<sub>i</sub>, length<sub>i</sub>, height<sub>i</sub>]</code> (<strong>0-indexed</strong>). Choose a <strong>subset</strong> of <code>cuboids</code> and place them on each other.</p>

<p>You can place cuboid <code>i</code> on cuboid <code>j</code> if <code>width<sub>i</sub> &lt;= width<sub>j</sub></code> and <code>length<sub>i</sub> &lt;= length<sub>j</sub></code> and <code>height<sub>i</sub> &lt;= height<sub>j</sub></code>. You can rearrange any cuboid&#39;s dimensions by rotating it to put it on another cuboid.</p>

<p>Return <em>the <strong>maximum height</strong> of the stacked</em> <code>cuboids</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/10/21/image.jpg" style="width: 420px; height: 299px;" /></strong></p>

<pre>
<strong>Input:</strong> cuboids = [[50,45,20],[95,37,53],[45,23,12]]
<strong>Output:</strong> 190
<strong>Explanation:</strong>
Cuboid 1 is placed on the bottom with the 53x37 side facing down with height 95.
Cuboid 0 is placed next with the 45x20 side facing down with height 50.
Cuboid 2 is placed next with the 23x12 side facing down with height 45.
The total height is 95 + 50 + 45 = 190.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> cuboids = [[38,25,45],[76,35,3]]
<strong>Output:</strong> 76
<strong>Explanation:</strong>
You can&#39;t place any of the cuboids on the other.
We choose cuboid 1 and rotate it so that the 35x3 side is facing down and its height is 76.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> cuboids = [[7,11,17],[7,17,11],[11,7,17],[11,17,7],[17,7,11],[17,11,7]]
<strong>Output:</strong> 102
<strong>Explanation:</strong>
After rearranging the cuboids, you can see that all cuboids have the same dimension.
You can place the 11x7 side down on all cuboids so their heights are 17.
The maximum height of stacked cuboids is 6 * 17 = 102.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == cuboids.length</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>1 &lt;= width<sub>i</sub>, length<sub>i</sub>, height<sub>i</sub> &lt;= 100</code></li>
</ul>
 instead-->
<p>给你 <code>n</code> 个长方体 <code>cuboids</code> ，其中第 <code>i</code> 个长方体的长宽高表示为 <code>cuboids[i] = [width<sub>i</sub>, length<sub>i</sub>, height<sub>i</sub>]</code>（<strong>下标从 0 开始</strong>）。请你从 <code>cuboids</code> 选出一个 <strong>子集</strong> ，并将它们堆叠起来。</p>

<p>如果 <code>width<sub>i</sub> <= width<sub>j</sub></code> 且 <code>length<sub>i</sub> <= length<sub>j</sub></code> 且 <code>height<sub>i</sub> <= height<sub>j</sub></code> ，你就可以将长方体 <code>i</code> 堆叠在长方体 <code>j</code> 上。你可以通过旋转把长方体的长宽高重新排列，以将它放在另一个长方体上。</p>

<p>返回 <strong>堆叠长方体</strong> <code>cuboids</code> 可以得到的 <strong>最大高度</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/12/12/image.jpg" style="width: 420px; height: 299px;" /></strong></p>

<pre>
<strong>输入：</strong>cuboids = [[50,45,20],[95,37,53],[45,23,12]]
<strong>输出：</strong>190
<strong>解释：</strong>
第 1 个长方体放在底部，53x37 的一面朝下，高度为 95 。
第 0 个长方体放在中间，45x20 的一面朝下，高度为 50 。
第 2 个长方体放在上面，23x12 的一面朝下，高度为 45 。
总高度是 95 + 50 + 45 = 190 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>cuboids = [[38,25,45],[76,35,3]]
<strong>输出：</strong>76
<strong>解释：</strong>
无法将任何长方体放在另一个上面。
选择第 1 个长方体然后旋转它，使 35x3 的一面朝下，其高度为 76 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>cuboids = [[7,11,17],[7,17,11],[11,7,17],[11,17,7],[17,7,11],[17,11,7]]
<strong>输出：</strong>102
<strong>解释：</strong>
重新排列长方体后，可以看到所有长方体的尺寸都相同。
你可以把 11x7 的一面朝下，这样它们的高度就是 17 。
堆叠长方体的最大高度为 6 * 17 = 102 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == cuboids.length</code></li>
	<li><code>1 <= n <= 100</code></li>
	<li><code>1 <= width<sub>i</sub>, length<sub>i</sub>, height<sub>i</sub> <= 100</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int maxHeight(int[][] cuboids) {
        int n = cuboids.length;//长方体的个数

        /***************************/
        /*********预处理************/
        /***************************/
        //1.先将长方体按照统一的姿势摆放
        for(int[] num:cuboids)Arrays.sort(num);
        //2.再将摆放好的长方体按照对应的【长宽高】进行排序
        Arrays.sort(cuboids,(a,b)->(a[0]==b[0]?(a[1]==b[1]?a[2]-b[2]:a[1]-b[1]):a[0]-b[0]));

        int ans = 0;//记录结果
        int[] dp = new int[n];//记录以第i个长方体为底的符合规范的高度
        dp[0] = cuboids[0][2];ans = dp[0];//初始化

        /***************************/
        /*********执行操作**********/
        /***************************/
        //3.对第i个长方体执行以下操作：
        //      以此长方体为底，遍历前面已经堆叠好的长方体，找到一个最高且符合规范的，放在此长方体上面
        for(int i = 1;i < n;i++){
            for(int j = i-1;j > -1;j--){
                if(cuboids[j][1]<=cuboids[i][1]&&cuboids[j][2]<=cuboids[i][2])dp[i] = Math.max(dp[i],dp[j]);
            }
            dp[i]+=cuboids[i][2];//使用dp数组记录当前堆叠的长方体的高度
            ans = Math.max(ans,dp[i]);//使用ans来记录最高的那一组长方体
        }

        return ans;//返回结果
    }
}
//注：此题与最长递增子序列、俄罗斯套娃信封问题同属一种问题
//注：需要注意的是在这之间的排序的问题


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-height-by-stacking-cuboids/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-height-by-stacking-cuboids/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-height-by-stacking-cuboids/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-height-by-stacking-cuboids/)

[回到目录](../README.md)