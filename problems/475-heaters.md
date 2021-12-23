# 475. heaters | 供暖器

## Question description

<!--If you want to use the English description, use <p>Winter is coming! During the contest, your first job is to design a standard heater with a fixed warm radius to warm all the houses.</p>

<p>Every house can be warmed, as long as the house is within the heater&#39;s warm radius range.&nbsp;</p>

<p>Given the positions of <code>houses</code> and <code>heaters</code> on a horizontal line, return <em>the minimum radius standard of heaters&nbsp;so that those heaters could cover all houses.</em></p>

<p><strong>Notice</strong> that&nbsp;all the <code>heaters</code> follow your radius standard, and the warm radius will the same.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> houses = [1,2,3], heaters = [2]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The only heater was placed in the position 2, and if we use the radius 1 standard, then all the houses can be warmed.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> houses = [1,2,3,4], heaters = [1,4]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The two heater was placed in the position 1 and 4. We need to use radius 1 standard, then all the houses can be warmed.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> houses = [1,5], heaters = [2]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= houses.length, heaters.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= houses[i], heaters[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>冬季已经来临。 你的任务是设计一个有固定加热半径的供暖器向所有房屋供暖。</p>

<p>在加热器的加热半径范围内的每个房屋都可以获得供暖。</p>

<p>现在，给出位于一条水平线上的房屋 <code>houses</code> 和供暖器 <code>heaters</code> 的位置，请你找出并返回可以覆盖所有房屋的最小加热半径。</p>

<p><strong>说明</strong>：所有供暖器都遵循你的半径标准，加热的半径也一样。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> houses = [1,2,3], heaters = [2]
<strong>输出:</strong> 1
<strong>解释:</strong> 仅在位置2上有一个供暖器。如果我们将加热半径设为1，那么所有房屋就都能得到供暖。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> houses = [1,2,3,4], heaters = [1,4]
<strong>输出:</strong> 1
<strong>解释:</strong> 在位置1, 4上有两个供暖器。我们需要将加热半径设为1，这样所有房屋就都能得到供暖。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>houses = [1,5], heaters = [2]
<strong>输出：</strong>3
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= houses.length, heaters.length <= 3 * 10<sup>4</sup></code></li>
	<li><code>1 <= houses[i], heaters[i] <= 10<sup>9</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 10 ms

```java
class Solution {
        // 贪心 + 排序 + 双指针（不回退）
    public static int findRadius(int[] houses, int[] heaters) {
        Arrays.sort(houses);
        Arrays.sort(heaters);
        int i = 0, j = 0, ans = 0; // 双指针
        while (i < houses.length) {
            int minDistance = 0;
            if (j == heaters.length-1) {
                minDistance = Math.abs(heaters[j] - houses[i++]);
            } else {
                int distance1 = Math.abs(heaters[j] - houses[i]);
                int distance2 = Math.abs(heaters[j+1] - houses[i]);
                if (distance1 >= distance2) j++;
                else { // 当前j位置是给i位置供暖的最优点
                    minDistance = distance1;
                    i++;
                }
            }
            ans = Math.max(ans, minDistance);
        }
        return ans;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/heaters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/heaters/description/)

Solution: [LeetCode](https://leetcode.com/articles/heaters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/heaters/)

[回到目录](../README.md)