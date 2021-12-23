# 剑指 Offer II 079. TVdhkn | 所有子集

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个整数数组&nbsp;<code>nums</code> ，数组中的元素 <strong>互不相同</strong> 。返回该数组所有可能的子集（幂集）。</p>

<p>解集 <strong>不能</strong> 包含重复的子集。你可以按 <strong>任意顺序</strong> 返回解集。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3]
<strong>输出：</strong>[[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [0]
<strong>输出：</strong>[[],[0]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10</code></li>
	<li><code>-10 &lt;= nums[i] &lt;= 10</code></li>
	<li><code>nums</code> 中的所有元素 <strong>互不相同</strong></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 78&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/subsets/">https://leetcode-cn.com/problems/subsets/</a></p>




## Solution

Language: **java**  /  Runtime: 13 ms

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>>list=new ArrayList<List<Integer>>();
        List<Integer>temp=new ArrayList<Integer>();
        Arrays.sort(nums);
        int len=nums.length;
        for(int i=0;i<1<<len;i++) {
            temp.clear();
            for(int j=0;j<len;j++) {
                int t=(i>>j)&1;
                if(t==1){
                    temp.add(nums[j]);
                    System.out.println(nums[j]);
                }
            }
            list.add(new ArrayList<Integer>(temp));
        }
        return list;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/TVdhkn/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/TVdhkn/description/)

Solution: [LeetCode](https://leetcode.com/articles/TVdhkn/)  /  [LeetCode中国](https://leetcode-cn.com/articles/TVdhkn/)

[回到目录](../README.md)