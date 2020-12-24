# 78. subsets | 子集

## Question description

<!--If you want to use the English description, use <p>Given an&nbsp;integer array&nbsp;<code>nums</code>, return <em>all possible subsets (the power set)</em>.</p>

<p>The solution set must not contain duplicate subsets.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0]
<strong>Output:</strong> [[],[0]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10</code></li>
	<li><code>-10 &lt;= nums[i] &lt;= 10</code></li>
</ul>
 instead-->
<p>给定一组<strong>不含重复元素</strong>的整数数组&nbsp;<em>nums</em>，返回该数组所有可能的子集（幂集）。</p>

<p><strong>说明：</strong>解集不能包含重复的子集。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> nums = [1,2,3]
<strong>输出:</strong>
[
  [3],
&nbsp; [1],
&nbsp; [2],
&nbsp; [1,2,3],
&nbsp; [1,3],
&nbsp; [2,3],
&nbsp; [1,2],
&nbsp; []
]</pre>


## Note

1 迭代法实现子集枚举



2 递归法实现子集合枚举


## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    vector<int> t;
    vector<vector<int>> ans;

    void dfs(int cur, vector<int>& nums) {
        if (cur == nums.size()) {
            ans.push_back(t);
            return;
        }
        t.push_back(nums[cur]);
        dfs(cur + 1, nums);
        t.pop_back();
        dfs(cur + 1, nums);
    }

    vector<vector<int>> subsets(vector<int>& nums) {
        dfs(0, nums);
        return ans;
    }
};


```

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    List<Integer> t = new ArrayList<Integer>();
    List<List<Integer>> ans = new ArrayList<List<Integer>>();

    public List<List<Integer>> subsets(int[] nums) {
        int n = nums.length;
        for (int mask = 0; mask < (1 << n); ++mask) {
            t.clear();
            for (int i = 0; i < n; ++i) {
                if ((mask & (1 << i)) != 0) {
                    t.add(nums[i]);
                }
            }
            ans.add(new ArrayList<Integer>(t));
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/subsets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subsets/description/)

Solution: [LeetCode](https://leetcode.com/articles/subsets/)  /  [LeetCode中国](https://leetcode-cn.com/articles/subsets/)

[回到目录](../README.md)