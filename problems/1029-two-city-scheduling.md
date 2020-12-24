# 1029. two-city-scheduling | 两地调度

## Question description

<!--If you want to use the English description, use <p>A company is planning to interview <code>2n</code> people. Given the array <code>costs</code> where <code>costs[i] = [aCost<sub>i</sub>, bCost<sub>i</sub>]</code>,&nbsp;the cost of flying the <code>i<sup>th</sup></code> person to city <code>a</code> is <code>aCost<sub>i</sub></code>, and the cost of flying the <code>i<sup>th</sup></code> person to city <code>b</code> is <code>bCost<sub>i</sub></code>.</p>

<p>Return <em>the minimum cost to fly every person to a city</em> such that exactly <code>n</code> people arrive in each city.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> costs = [[10,20],[30,200],[400,50],[30,20]]
<strong>Output:</strong> 110
<strong>Explanation: </strong>
The first person goes to city A for a cost of 10.
The second person goes to city A for a cost of 30.
The third person goes to city B for a cost of 50.
The fourth person goes to city B for a cost of 20.

The total minimum cost is 10 + 30 + 50 + 20 = 110 to have half the people interviewing in each city.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> costs = [[259,770],[448,54],[926,667],[184,139],[840,118],[577,469]]
<strong>Output:</strong> 1859
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> costs = [[515,563],[451,713],[537,709],[343,819],[855,779],[457,60],[650,359],[631,42]]
<strong>Output:</strong> 3086
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 * n == costs.length</code></li>
	<li><code>2 &lt;= costs.length &lt;= 100</code></li>
	<li><code>costs.length</code> is even.</li>
	<li><code>1 &lt;= aCost<sub>i</sub>, bCost<sub>i</sub> &lt;= 1000</code></li>
</ul>
 instead-->
<p>公司计划面试 <code>2N</code> 人。第 <code>i</code> 人飞往 <code>A</code> 市的费用为 <code>costs[i][0]</code>，飞往 <code>B</code> 市的费用为 <code>costs[i][1]</code>。</p>

<p>返回将每个人都飞到某座城市的最低费用，要求每个城市都有 <code>N</code> 人抵达<strong>。</strong></p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[[10,20],[30,200],[400,50],[30,20]]
<strong>输出：</strong>110
<strong>解释：</strong>
第一个人去 A 市，费用为 10。
第二个人去 A 市，费用为 30。
第三个人去 B 市，费用为 50。
第四个人去 B 市，费用为 20。

最低总费用为 10 + 30 + 50 + 20 = 110，每个城市都有一半的人在面试。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= costs.length &lt;= 100</code></li>
	<li><code>costs.length</code> 为偶数</li>
	<li><code>1 &lt;= costs[i][0], costs[i][1] &lt;= 1000</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int twoCitySchedCost(int[][] costs) {
      // Sort by a gain which company has 
      // by sending a person to city A and not to city B
      Arrays.sort(costs, new Comparator<int[]>() {
          @Override
          public int compare(int[] o1, int[] o2) {
              return o1[0] - o1[1] - (o2[0] - o2[1]);
          }
      });

      int total = 0;
      int n = costs.length / 2;
      // To optimize the company expenses,
      // send the first n persons to the city A
      // and the others to the city B
      for (int i = 0; i < n; ++i) total += costs[i][0] + costs[i + n][1];
      return total;
    }
}


```

Language: **python3**  /  Runtime: 96 ms

```python3
class Solution:
    def twoCitySchedCost(self, costs: List[List[int]]) -> int:
        # Sort by a gain which company has 
        # by sending a person to city A and not to city B
        costs.sort(key = lambda x : x[0] - x[1])
        
        total = 0
        n = len(costs) // 2
        # To optimize the company expenses,
        # send the first n persons to the city A
        # and the others to the city B
        for i in range(n):
            total += costs[i][0] + costs[i + n][1]
        return total


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/two-city-scheduling/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/two-city-scheduling/description/)

Solution: [LeetCode](https://leetcode.com/articles/two-city-scheduling/)  /  [LeetCode中国](https://leetcode-cn.com/articles/two-city-scheduling/)

[回到目录](../README.md)