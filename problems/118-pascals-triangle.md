# 118. pascals-triangle | 杨辉三角

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>numRows</code>, return the first numRows of <strong>Pascal&#39;s triangle</strong>.</p>

<p>In <strong>Pascal&#39;s triangle</strong>, each number is the sum of the two numbers directly above it as shown:</p>
<img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" style="height:240px; width:260px" />
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> numRows = 5
<strong>Output:</strong> [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> numRows = 1
<strong>Output:</strong> [[1]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= numRows &lt;= 30</code></li>
</ul>
 instead-->
<p>给定一个非负整数 <em><code>numRows</code>，</em>生成「杨辉三角」的前 <em><code>numRows</code> </em>行。</p>

<p><small>在「杨辉三角」中，每个数是它左上方和右上方的数的和。</small></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626927345-DZmfxB-PascalTriangleAnimated2.gif" /></p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> numRows = 5
<strong>输出:</strong> [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> numRows = 1
<strong>输出:</strong> [[1]]
</pre>

<p> </p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 <= numRows <= 30</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>>res=new ArrayList<>();
        List<Integer>list=new ArrayList<>();
        list.add(1);
        res.add(new ArrayList<>(list));
        if(numRows==1)return res;
        for(int i=1;i<numRows;i++){
            //list.clear();
            List<Integer>temp=new ArrayList<>();
            temp.add(1);
            for(int j=1;j<i;j++){
                temp.add(list.get(j-1)+list.get(j));
            }
            temp.add(1);
            
            list.clear();
            list=temp;
            res.add(new ArrayList<>(list));
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/pascals-triangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pascals-triangle/description/)

Solution: [LeetCode](https://leetcode.com/articles/pascals-triangle/)  /  [LeetCode中国](https://leetcode-cn.com/articles/pascals-triangle/)

[回到目录](../README.md)