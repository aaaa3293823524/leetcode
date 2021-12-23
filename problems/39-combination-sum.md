# 39. combination-sum | 组合总和

## Question description

<!--If you want to use the English description, use <p>Given an array of <strong>distinct</strong> integers <code>candidates</code> and a target integer <code>target</code>, return <em>a list of all <strong>unique combinations</strong> of </em><code>candidates</code><em> where the chosen numbers sum to </em><code>target</code><em>.</em> You may return the combinations in <strong>any order</strong>.</p>

<p>The <strong>same</strong> number may be chosen from <code>candidates</code> an <strong>unlimited number of times</strong>. Two combinations are unique if the frequency of at least one of the chosen numbers is different.</p>

<p>It is <strong>guaranteed</strong> that the number of unique combinations that sum up to <code>target</code> is less than <code>150</code> combinations for the given input.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> candidates = [2,3,6,7], target = 7
<strong>Output:</strong> [[2,2,3],[7]]
<strong>Explanation:</strong>
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> candidates = [2,3,5], target = 8
<strong>Output:</strong> [[2,2,2,2],[2,3,3],[3,5]]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> candidates = [2], target = 1
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= candidates.length &lt;= 30</code></li>
	<li><code>1 &lt;= candidates[i] &lt;= 200</code></li>
	<li>All elements of <code>candidates</code> are <strong>distinct</strong>.</li>
	<li><code>1 &lt;= target &lt;= 500</code></li>
</ul>
 instead-->
<p>给你一个 <strong>无重复元素</strong> 的整数数组&nbsp;<code>candidates</code> 和一个目标整数&nbsp;<code>target</code>&nbsp;，找出&nbsp;<code>candidates</code>&nbsp;中可以使数字和为目标数&nbsp;<code>target</code> 的 <strong>所有不同组合</strong> ，并以列表形式返回。你可以按 <strong>任意顺序</strong> 返回这些组合。</p>

<p><code>candidates</code> 中的 <strong>同一个</strong> 数字可以 <strong>无限制重复被选取</strong> 。如果至少一个数字的被选数量不同，则两种组合是不同的。&nbsp;</p>

<p>对于给定的输入，保证和为&nbsp;<code>target</code> 的不同组合数少于 <code>150</code> 个。</p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1：</strong></p>

<pre>
<strong>输入：</strong>candidates = <code>[2,3,6,7], </code>target = <code>7</code>
<strong>输出：</strong>[[2,2,3],[7]]
<strong>解释：</strong>
2 和 3 可以形成一组候选，2 + 2 + 3 = 7 。注意 2 可以使用多次。
7 也是一个候选， 7 = 7 。
仅有这两种组合。</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre>
<strong>输入: </strong>candidates = [2,3,5]<code>, </code>target = 8
<strong>输出: </strong>[[2,2,2,2],[2,3,3],[3,5]]</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入: </strong>candidates = <code>[2], </code>target = 1
<strong>输出: </strong>[]
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入: </strong>candidates = <code>[1], </code>target = <code>1</code>
<strong>输出: </strong>[[1]]
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入: </strong>candidates = <code>[1], </code>target = <code>2</code>
<strong>输出: </strong>[[1,1]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= candidates.length &lt;= 30</code></li>
	<li><code>1 &lt;= candidates[i] &lt;= 200</code></li>
	<li><code>candidate</code> 中的每个元素都 <strong>互不相同</strong></li>
	<li><code>1 &lt;= target &lt;= 500</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>>res=new ArrayList<List<Integer>>();
        List<Integer>list=new ArrayList<Integer>();
        
        dfs(0, candidates, target,list,res);
        return res;
    }
    
    public void dfs(int id,int[] candidates,int target,List<Integer>list,List<List<Integer>>res) {
        // for(int i=0;i<list.size();i++){
        //         System.out.print(list.get(i)+" ");
        //     }
        if(target==0) {
            res.add(new ArrayList<Integer>(list));
            return;
        }
        if(id>=candidates.length)return ;
        
        //for(int i=0;i<candidates.length;i++) {
            dfs(id+1, candidates, target,list,res);
            //System.out.println();
            for(int i=0;i<target/candidates[id];i++){
                list.add(candidates[id]);
                dfs(id+1, candidates, target-(i+1)*candidates[id],list,res);
                
            }
            for(int i=0;i<target/candidates[id];i++){
            list.remove(list.size()-1);
            }
            // list.add(candidates[id]);
            // dfs(id+1, candidates, target-candidates[id],list,res);
            // list.remove(list.size()-1);
            // dfs(id+1, candidates, target,list,res);
        //}
    }
}
```

Language: **python3**  /  Runtime: 116 ms

```python3
class Solution:
    def combinationSum(self, candidates, target):
        ans = []
        temp = []
        def recursion(idx, res):
            if idx >= len(candidates) or res >= target:
                if res == target:
                    ans.append(temp[:])
                return
            temp.append(candidates[idx])
            recursion(idx, res + candidates[idx]) 
            temp.pop()
            recursion(idx + 1, res)
        recursion(0, 0)
        return ans 
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/combination-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combination-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/combination-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/combination-sum/)

[回到目录](../README.md)