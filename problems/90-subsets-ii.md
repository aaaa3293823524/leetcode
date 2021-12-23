# 90. subsets-ii | 子集 II

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code> that may contain duplicates, return <em>all possible subsets (the power set)</em>.</p>

<p>The solution set <strong>must not</strong> contain duplicate subsets. Return the solution in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,2]
<strong>Output:</strong> [[],[1],[1,2],[1,2,2],[2],[2,2]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> [[],[0]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10</code></li>
	<li><code>-10 &lt;= nums[i] &lt;= 10</code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>nums</code> ，其中可能包含重复元素，请你返回该数组所有可能的子集（幂集）。</p>

<p>解集 <strong>不能</strong> 包含重复的子集。返回的解集中，子集可以按 <strong>任意顺序</strong> 排列。</p>

<div class="original__bRMd">
<div>
<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,2]
<strong>输出：</strong>[[],[1],[1,2],[1,2,2],[2],[2,2]]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [0]
<strong>输出：</strong>[[],[0]]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 10</code></li>
	<li><code>-10 <= nums[i] <= 10</code></li>
</ul>
</div>
</div>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>>res=new ArrayList<>();
        List<Integer>list=new ArrayList<>();
        boolean[]vis=new boolean[nums.length];
        Arrays.sort(nums);
        dfs(0,res,list,nums,vis);
        return res;
    }
    public void dfs(int id,List<List<Integer>>res,List<Integer>list,int[] nums,boolean[]vis){
        if(id==nums.length){
            res.add(new ArrayList<>(list));
            return;
        }
        dfs(id+1, res, list,nums,vis);
        if(id>0&&!vis[id-1]&&nums[id-1]==nums[id])return;
        list.add(nums[id]);
        vis[id]=true;
        dfs(id+1, res, list,nums,vis);
        list.remove(list.size()-1);
        vis[id]=false;
        
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/subsets-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subsets-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/subsets-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/subsets-ii/)

[回到目录](../README.md)