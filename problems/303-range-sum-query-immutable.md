# 303. range-sum-query-immutable | 区域和检索 - 数组不可变

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, handle multiple queries of the following type:</p>

<ol>
	<li>Calculate the <strong>sum</strong> of the elements of <code>nums</code> between indices <code>left</code> and <code>right</code> <strong>inclusive</strong> where <code>left &lt;= right</code>.</li>
</ol>

<p>Implement the <code>NumArray</code> class:</p>

<ul>
	<li><code>NumArray(int[] nums)</code> Initializes the object with the integer array <code>nums</code>.</li>
	<li><code>int sumRange(int left, int right)</code> Returns the <strong>sum</strong> of the elements of <code>nums</code> between indices <code>left</code> and <code>right</code> <strong>inclusive</strong> (i.e. <code>nums[left] + nums[left + 1] + ... + nums[right]</code>).</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input</strong>
[&quot;NumArray&quot;, &quot;sumRange&quot;, &quot;sumRange&quot;, &quot;sumRange&quot;]
[[[-2, 0, 3, -5, 2, -1]], [0, 2], [2, 5], [0, 5]]
<strong>Output</strong>
[null, 1, -1, -3]

<strong>Explanation</strong>
NumArray numArray = new NumArray([-2, 0, 3, -5, 2, -1]);
numArray.sumRange(0, 2); // return (-2) + 0 + 3 = 1
numArray.sumRange(2, 5); // return 3 + (-5) + 2 + (-1) = -1
numArray.sumRange(0, 5); // return (-2) + 0 + 3 + (-5) + 2 + (-1) = -3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>5</sup> &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= left &lt;= right &lt; nums.length</code></li>
	<li>At most <code>10<sup>4</sup></code> calls will be made to <code>sumRange</code>.</li>
</ul>
 instead-->
<p>给定一个整数数组  <code>nums</code>，求出数组从索引 <code>i</code><em> </em>到 <code>j</code>（<code>i ≤ j</code>）范围内元素的总和，包含 <code>i</code>、<code>j </code>两点。</p>

<div class="original__bRMd">
<div>
<p>实现 <code>NumArray</code> 类：</p>

<ul>
	<li><code>NumArray(int[] nums)</code> 使用数组 <code>nums</code> 初始化对象</li>
	<li><code>int sumRange(int i, int j)</code> 返回数组 <code>nums</code> 从索引 <code>i</code><em> </em>到 <code>j</code><em>（</em><code>i ≤ j</code>）范围内元素的总和，包含 <code>i</code>、<code>j </code>两点（也就是 <code>sum(nums[i], nums[i + 1], ... , nums[j])</code>）</li>
</ul>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>
["NumArray", "sumRange", "sumRange", "sumRange"]
[[[-2, 0, 3, -5, 2, -1]], [0, 2], [2, 5], [0, 5]]
<strong>输出：
</strong>[null, 1, -1, -3]

<strong>解释：</strong>
NumArray numArray = new NumArray([-2, 0, 3, -5, 2, -1]);
numArray.sumRange(0, 2); // return 1 ((-2) + 0 + 3)
numArray.sumRange(2, 5); // return -1 (3 + (-5) + 2 + (-1)) 
numArray.sumRange(0, 5); // return -3 ((-2) + 0 + 3 + (-5) + 2 + (-1))
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= nums.length <= 10<sup>4</sup></code></li>
	<li><code>-10<sup>5</sup> <= nums[i] <= 10<sup>5</sup></code></li>
	<li><code>0 <= i <= j < nums.length</code></li>
	<li>最多调用 <code>10<sup>4</sup></code> 次 <code>sumRange</code><strong> </strong>方法</li>
</ul>
</div>
</div>




## Solution

Language: **java**  /  Runtime: 70 ms

```java
class NumArray {
    int[]nums;
    public NumArray(int[] nums) {
        this.nums=nums;
    }
    
    public int sumRange(int left, int right) {
        int sum=0;
        for(int i=left;i<=right;i++){
            sum+=nums[i];
        }
        return sum;
    }
}

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * int param_1 = obj.sumRange(left,right);
 */
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/range-sum-query-immutable/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/range-sum-query-immutable/description/)

Solution: [LeetCode](https://leetcode.com/articles/range-sum-query-immutable/)  /  [LeetCode中国](https://leetcode-cn.com/articles/range-sum-query-immutable/)

[回到目录](../README.md)