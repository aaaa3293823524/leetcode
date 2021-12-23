# 492. construct-the-rectangle | 构造矩形

## Question description

<!--If you want to use the English description, use <p>A web developer needs to know how to design a web page&#39;s size. So, given a specific rectangular web page&rsquo;s area, your job by now is to design a rectangular web page, whose length L and width W satisfy the following requirements:</p>

<ol>
	<li>The area of the rectangular web page you designed must equal to the given target area.</li>
	<li>The width <code>W</code> should not be larger than the length <code>L</code>, which means <code>L &gt;= W</code>.</li>
	<li>The difference between length <code>L</code> and width <code>W</code> should be as small as possible.</li>
</ol>

<p>Return <em>an array <code>[L, W]</code> where <code>L</code> and <code>W</code> are the length and width of the&nbsp;web page you designed in sequence.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> area = 4
<strong>Output:</strong> [2,2]
<strong>Explanation:</strong> The target area is 4, and all the possible ways to construct it are [1,4], [2,2], [4,1]. 
But according to requirement 2, [1,4] is illegal; according to requirement 3,  [4,1] is not optimal compared to [2,2]. So the length L is 2, and the width W is 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> area = 37
<strong>Output:</strong> [37,1]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> area = 122122
<strong>Output:</strong> [427,286]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= area &lt;= 10<sup>7</sup></code></li>
</ul>
 instead-->
<p>作为一位web开发者， 懂得怎样去规划一个页面的尺寸是很重要的。 现给定一个具体的矩形页面面积，你的任务是设计一个长度为 L 和宽度为 W 且满足以下要求的矩形的页面。要求：</p>

<pre>
1. 你设计的矩形页面必须等于给定的目标面积。

2. 宽度 W 不应大于长度 L，换言之，要求 L &gt;= W 。

3. 长度 L 和宽度 W 之间的差距应当尽可能小。
</pre>

<p>你需要按顺序输出你设计的页面的长度 L 和宽度 W。</p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入:</strong> 4
<strong>输出:</strong> [2, 2]
<strong>解释:</strong> 目标面积是 4， 所有可能的构造方案有 [1,4], [2,2], [4,1]。
但是根据要求2，[1,4] 不符合要求; 根据要求3，[2,2] 比 [4,1] 更能符合要求. 所以输出长度 L 为 2， 宽度 W 为 2。
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>给定的面积不大于 10,000,000 且为正整数。</li>
	<li>你设计的页面的长度和宽度必须都是正整数。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int[] constructRectangle(int area) {
        int w = (int) Math.sqrt(area);
        while (area % w != 0) {
            --w;
        }
        return new int[]{area / w, w};
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/construct-the-rectangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/construct-the-rectangle/description/)

Solution: [LeetCode](https://leetcode.com/articles/construct-the-rectangle/)  /  [LeetCode中国](https://leetcode-cn.com/articles/construct-the-rectangle/)

[回到目录](../README.md)