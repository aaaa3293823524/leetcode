# 1552. magnetic-force-between-two-balls | 两球之间的磁力

## Question description

<!--If you want to use the English description, use <p>In the universe Earth C-137, Rick discovered a special form of magnetic force between two balls if they are put in his new invented basket. Rick has <code>n</code> empty baskets, the <code>i<sup>th</sup></code> basket is at <code>position[i]</code>, Morty has <code>m</code> balls and needs to distribute the balls into the baskets such that the <strong>minimum magnetic force</strong> between any two balls is <strong>maximum</strong>.</p>

<p>Rick stated that magnetic force between two different balls at positions <code>x</code> and <code>y</code> is <code>|x - y|</code>.</p>

<p>Given the integer array <code>position</code> and the integer <code>m</code>. Return <em>the required force</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/11/q3v1.jpg" style="width: 562px; height: 195px;" />
<pre>
<strong>Input:</strong> position = [1,2,3,4,7], m = 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> Distributing the 3 balls into baskets 1, 4 and 7 will make the magnetic force between ball pairs [3, 3, 6]. The minimum magnetic force is 3. We cannot achieve a larger minimum magnetic force than 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> position = [5,4,3,2,1,1000000000], m = 2
<strong>Output:</strong> 999999999
<strong>Explanation:</strong> We can use baskets 1 and 1000000000.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == position.length</code></li>
	<li><code>2 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= position[i] &lt;= 10<sup>9</sup></code></li>
	<li>All integers in <code>position</code> are <strong>distinct</strong>.</li>
	<li><code>2 &lt;= m &lt;= position.length</code></li>
</ul>
 instead-->
<p>在代号为 C-137 的地球上，Rick 发现如果他将两个球放在他新发明的篮子里，它们之间会形成特殊形式的磁力。Rick 有&nbsp;<code>n</code>&nbsp;个空的篮子，第&nbsp;<code>i</code>&nbsp;个篮子的位置在&nbsp;<code>position[i]</code>&nbsp;，Morty&nbsp;想把&nbsp;<code>m</code>&nbsp;个球放到这些篮子里，使得任意两球间&nbsp;<strong>最小磁力</strong>&nbsp;最大。</p>

<p>已知两个球如果分别位于&nbsp;<code>x</code>&nbsp;和&nbsp;<code>y</code>&nbsp;，那么它们之间的磁力为&nbsp;<code>|x - y|</code>&nbsp;。</p>

<p>给你一个整数数组&nbsp;<code>position</code>&nbsp;和一个整数&nbsp;<code>m</code>&nbsp;，请你返回最大化的最小磁力。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/16/q3v1.jpg" style="height: 195px; width: 562px;"></p>

<pre><strong>输入：</strong>position = [1,2,3,4,7], m = 3
<strong>输出：</strong>3
<strong>解释：</strong>将 3 个球分别放入位于 1，4 和 7 的三个篮子，两球间的磁力分别为 [3, 3, 6]。最小磁力为 3 。我们没办法让最小磁力大于 3 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>position = [5,4,3,2,1,1000000000], m = 2
<strong>输出：</strong>999999999
<strong>解释：</strong>我们使用位于 1 和 1000000000 的篮子时最小磁力最大。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == position.length</code></li>
	<li><code>2 &lt;= n &lt;= 10^5</code></li>
	<li><code>1 &lt;= position[i] &lt;= 10^9</code></li>
	<li>所有&nbsp;<code>position</code>&nbsp;中的整数 <strong>互不相同</strong>&nbsp;。</li>
	<li><code>2 &lt;= m &lt;= position.length</code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 152 ms

```cpp
class Solution {
public:
    bool check(vector<int> position, int middle_length, int m) {
        int count = 0;
        int i = 0;
        for (int j = 1; j < position.size(); j++) {
            if (position[j] - position[i] >= middle_length) {
                i = j;
                count++;
                if (count >= m - 1)
                    return true;
            }
        }
        return false;
    }
    int maxDistance(vector<int>& position, int m) {
        sort(position.begin(), position.end());
        int max_length = (position.back() - position.front()) / (m - 1);
        int min_length = 1;
        int ans = 1;
        while (min_length <= max_length) {
            int middle_length = (max_length + min_length) / 2;
            if (check(position, middle_length, m)) {
                ans = middle_length;
                min_length = middle_length + 1;
            } else max_length = middle_length - 1;
        }
        return ans;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/magnetic-force-between-two-balls/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/magnetic-force-between-two-balls/description/)

Solution: [LeetCode](https://leetcode.com/articles/magnetic-force-between-two-balls/)  /  [LeetCode中国](https://leetcode-cn.com/articles/magnetic-force-between-two-balls/)

[回到目录](../README.md)