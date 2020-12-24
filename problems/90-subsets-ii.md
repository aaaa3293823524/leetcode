# 90. subsets-ii | 子集 II

## Question description

<!--If you want to use the English description, use <p>Given a collection of integers that might contain duplicates, <strong><em>nums</em></strong>, return all possible subsets (the power set).</p>

<p><strong>Note:</strong> The solution set must not contain duplicate subsets.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,2,2]
<strong>Output:</strong>
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
</pre>
 instead-->
<p>给定一个可能包含重复元素的整数数组 <em><strong>nums</strong></em>，返回该数组所有可能的子集（幂集）。</p>

<p><strong>说明：</strong>解集不能包含重复的子集。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,2]
<strong>输出:</strong>
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]</pre>




## Solution

Language: **java**  /  Runtime: 24 ms

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<Integer> list1=new ArrayList<>();
        List<List<Integer>> list2=new ArrayList<>();
        Set<List<Integer>>set=new HashSet<>();
        Arrays.sort(nums);
        for(int mask=1;mask<=(1<<nums.length);mask++){
            list1.clear();
            for(int i=0;i<nums.length;i++){
                if((mask&(1<<i))!=0){
                    list1.add(nums[i]);
            }
            if(!list2.contains(list1)){
                list2.add(new ArrayList(list1));
            }
            
            }
            
        }
        return list2;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/subsets-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subsets-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/subsets-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/subsets-ii/)

[回到目录](../README.md)