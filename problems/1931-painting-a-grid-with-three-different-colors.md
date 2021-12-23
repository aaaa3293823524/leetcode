# 1931. painting-a-grid-with-three-different-colors | 用三种不同颜色为网格涂色

## Question description

<!--If you want to use the English description, use <p>You are given two integers <code>m</code> and <code>n</code>. Consider an <code>m x n</code> grid where each cell is initially white. You can paint each cell <strong>red</strong>, <strong>green</strong>, or <strong>blue</strong>. All cells <strong>must</strong> be painted.</p>

<p>Return<em> the number of ways to color the grid with <strong>no two adjacent cells having the same color</strong></em>. Since the answer can be very large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/22/colorthegrid.png" style="width: 200px; height: 50px;" />
<pre>
<strong>Input:</strong> m = 1, n = 1
<strong>Output:</strong> 3
<strong>Explanation:</strong> The three possible colorings are shown in the image above.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/22/copy-of-colorthegrid.png" style="width: 321px; height: 121px;" />
<pre>
<strong>Input:</strong> m = 1, n = 2
<strong>Output:</strong> 6
<strong>Explanation:</strong> The six possible colorings are shown in the image above.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> m = 5, n = 5
<strong>Output:</strong> 580986
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= m &lt;= 5</code></li>
	<li><code>1 &lt;= n &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你两个整数 <code>m</code> 和 <code>n</code> 。构造一个 <code>m x n</code> 的网格，其中每个单元格最开始是白色。请你用 <strong>红、绿、蓝</strong> 三种颜色为每个单元格涂色。所有单元格都需要被涂色。</p>

<p>涂色方案需要满足：<strong>不存在相邻两个单元格颜色相同的情况</strong> 。返回网格涂色的方法数。因为答案可能非常大， 返回 <strong>对 </strong><code>10<sup>9</sup> + 7</code><strong> 取余</strong> 的结果。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/22/colorthegrid.png" style="width: 200px; height: 50px;" />
<pre>
<strong>输入：</strong>m = 1, n = 1
<strong>输出：</strong>3
<strong>解释：</strong>如上图所示，存在三种可能的涂色方案。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/22/copy-of-colorthegrid.png" style="width: 321px; height: 121px;" />
<pre>
<strong>输入：</strong>m = 1, n = 2
<strong>输出：</strong>6
<strong>解释：</strong>如上图所示，存在六种可能的涂色方案。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>m = 5, n = 5
<strong>输出：</strong>580986
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= m <= 5</code></li>
	<li><code>1 <= n <= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 45 ms

```java
class Solution {
    public int colorTheGrid(int m, int n) {
        final int MOD = 1_000_000_007;
        // key 为有效的 mask 值，value 为 mask 值对应的 3 进制数
        Map<Integer, int[]> valid = new HashMap<>();
        int maskEnd = (int)Math.pow(3, m);

        // 初始化 valid 
        for(int mask = 0; mask < maskEnd; ++mask){
            int[] color = new int[m];
            int mm = mask;
            // 分析三进制值，如果相邻两个值相同，则不符合要求，舍弃
            boolean check = true;
            for(int i = 0; i < m; ++i){
                color[i] = mm % 3;
                if(i > 0 && color[i-1] == color[i]) check = false;
                mm /= 3;
            }
            if(check) valid.put(mask, color);  
        }

        // 预处理，分析所有可能相邻的二元组，将该信息放置在 map 中
        // key 值为 mask 值，value 为可与该 mask 相邻的 mask 值列表
        Map<Integer, List<Integer>> adjacent = new HashMap<>();
        for(Integer mask1 : valid.keySet()){
            List<Integer> list = new ArrayList<>();
            for(Integer mask2 : valid.keySet()){
                boolean check = true;
                for(int i = 0; i < m; ++i){
                    if(valid.get(mask1)[i] == valid.get(mask2)[i]){
                        check = false;
                        break;
                    }
                }
                if(check) list.add(mask2);
            }
            adjacent.put(mask1, list);
        }

        // 由于 dp[i][mask] 仅与 dp[i-1][mask'] 有关，因此，可以使用一维数组实现 dp
        int[] dp = new int[maskEnd];

        // 边界条件：dp[i][mask], i == 0 时
        for(Integer mask : valid.keySet()){
            dp[mask] = 1;
        }

        // 动态规划
        for(int i = 1; i < n; ++i){
            int[] tmpDp = new int[maskEnd];
            for(Integer mask : valid.keySet()){
                for(Integer index : adjacent.get(mask)){
                    tmpDp[mask] += dp[index];
                    tmpDp[mask] %= MOD;
                }
            }
            dp = tmpDp;
        }
        
        int ans = 0;
        for(Integer mask : valid.keySet()){
            ans += dp[mask];
            ans %= MOD;
        }
        return ans;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/painting-a-grid-with-three-different-colors/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/painting-a-grid-with-three-different-colors/description/)

Solution: [LeetCode](https://leetcode.com/articles/painting-a-grid-with-three-different-colors/)  /  [LeetCode中国](https://leetcode-cn.com/articles/painting-a-grid-with-three-different-colors/)

[回到目录](../README.md)