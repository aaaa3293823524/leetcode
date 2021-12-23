# 1547. minimum-cost-to-cut-a-stick | 切棍子的最小成本

## Question description

<!--If you want to use the English description, use <p>Given a wooden stick of length <code>n</code> units. The stick is labelled from <code>0</code> to <code>n</code>. For example, a stick of length <strong>6</strong> is labelled as follows:</p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/07/21/statement.jpg" style="width: 521px; height: 111px;" />
<p>Given an integer array <code>cuts</code> where <code>cuts[i]</code> denotes a position you should perform a cut at.</p>

<p>You should perform the cuts in order, you can change the order of the cuts as you wish.</p>

<p>The cost of one cut is the length of the stick to be cut, the total cost is the sum of costs of all cuts. When you cut a stick, it will be split into two smaller sticks (i.e. the sum of their lengths is the length of the stick before the cut). Please refer to the first example for a better explanation.</p>

<p>Return <em>the minimum total cost</em> of the cuts.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/07/23/e1.jpg" style="width: 350px; height: 284px;" />
<pre>
<strong>Input:</strong> n = 7, cuts = [1,3,4,5]
<strong>Output:</strong> 16
<strong>Explanation:</strong> Using cuts order = [1, 3, 4, 5] as in the input leads to the following scenario:
<img alt="" src="https://assets.leetcode.com/uploads/2020/07/21/e11.jpg" style="width: 350px; height: 284px;" />
The first cut is done to a rod of length 7 so the cost is 7. The second cut is done to a rod of length 6 (i.e. the second part of the first cut), the third is done to a rod of length 4 and the last cut is to a rod of length 3. The total cost is 7 + 6 + 4 + 3 = 20.
Rearranging the cuts to be [3, 5, 1, 4] for example will lead to a scenario with total cost = 16 (as shown in the example photo 7 + 4 + 3 + 2 = 16).</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 9, cuts = [5,6,1,4,2]
<strong>Output:</strong> 22
<strong>Explanation:</strong> If you try the given cuts ordering the cost will be 25.
There are much ordering with total cost &lt;= 25, for example, the order [4, 6, 5, 2, 1] has total cost = 22 which is the minimum possible.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= n &lt;= 10<sup>6</sup></code></li>
	<li><code>1 &lt;= cuts.length &lt;= min(n - 1, 100)</code></li>
	<li><code>1 &lt;= cuts[i] &lt;= n - 1</code></li>
	<li>All the integers in <code>cuts</code> array are <strong>distinct</strong>.</li>
</ul>
 instead-->
<p>有一根长度为 <code>n</code> 个单位的木棍，棍上从 <code>0</code> 到 <code>n</code> 标记了若干位置。例如，长度为 <strong>6</strong> 的棍子可以标记如下：</p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/09/statement.jpg" style="height: 111px; width: 521px;" /></p>

<p>给你一个整数数组 <code>cuts</code> ，其中 <code>cuts[i]</code> 表示你需要将棍子切开的位置。</p>

<p>你可以按顺序完成切割，也可以根据需要更改切割的顺序。</p>

<p>每次切割的成本都是当前要切割的棍子的长度，切棍子的总成本是历次切割成本的总和。对棍子进行切割将会把一根木棍分成两根较小的木棍（这两根木棍的长度和就是切割前木棍的长度）。请参阅第一个示例以获得更直观的解释。</p>

<p>返回切棍子的 <strong>最小总成本</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/09/e1.jpg" style="height: 284px; width: 350px;" /></p>

<pre>
<strong>输入：</strong>n = 7, cuts = [1,3,4,5]
<strong>输出：</strong>16
<strong>解释：</strong>按 [1, 3, 4, 5] 的顺序切割的情况如下所示：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/09/e11.jpg" style="height: 284px; width: 350px;" />
第一次切割长度为 7 的棍子，成本为 7 。第二次切割长度为 6 的棍子（即第一次切割得到的第二根棍子），第三次切割为长度 4 的棍子，最后切割长度为 3 的棍子。总成本为 7 + 6 + 4 + 3 = 20 。
而将切割顺序重新排列为 [3, 5, 1, 4] 后，总成本 = 16（如示例图中 7 + 4 + 3 + 2 = 16）。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 9, cuts = [5,6,1,4,2]
<strong>输出：</strong>22
<strong>解释：</strong>如果按给定的顺序切割，则总成本为 25 。总成本 <= 25 的切割顺序很多，例如，[4, 6, 5, 2, 1] 的总成本 = 22，是所有可能方案中成本最小的。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 <= n <= 10^6</code></li>
	<li><code>1 <= cuts.length <= min(n - 1, 100)</code></li>
	<li><code>1 <= cuts[i] <= n - 1</code></li>
	<li><code>cuts</code> 数组中的所有整数都 <strong>互不相同</strong></li>
</ul>




## Solution

Language: **java**  /  Runtime: 12 ms

```java
class Solution {
    public int minCost(int n, int[] cuts) {
        int m = cuts.length;
        Arrays.sort(cuts);
        int[] newCuts = new int[m + 2];
        newCuts[0] = 0;
        for (int i = 1; i <= m; ++i) {
            newCuts[i] = cuts[i - 1];
        }
        newCuts[m + 1] = n;
        int[][] f = new int[m + 2][m + 2];
        for (int i = m; i >= 1; --i) {
            for (int j = i; j <= m; ++j) {
                f[i][j] = i == j ? 0 : Integer.MAX_VALUE;
                for (int k = i; k <= j; ++k) {
                    f[i][j] = Math.min(f[i][j], f[i][k - 1] + f[k + 1][j]);
                }
                f[i][j] += newCuts[j + 1] - newCuts[i - 1];
            }
        }
        return f[1][m];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-cost-to-cut-a-stick/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-cost-to-cut-a-stick/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-cost-to-cut-a-stick/)

[回到目录](../README.md)