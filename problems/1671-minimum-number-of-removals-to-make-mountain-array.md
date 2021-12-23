# 1671. minimum-number-of-removals-to-make-mountain-array | 得到山形数组的最少删除次数

## Question description

<!--If you want to use the English description, use <p>You may recall that an array <code>arr</code> is a <strong>mountain array</strong> if and only if:</p>

<ul>
	<li><code>arr.length &gt;= 3</code></li>
	<li>There exists some index <code>i</code> (<strong>0-indexed</strong>) with <code>0 &lt; i &lt; arr.length - 1</code> such that:
	<ul>
		<li><code>arr[0] &lt; arr[1] &lt; ... &lt; arr[i - 1] &lt; arr[i]</code></li>
		<li><code>arr[i] &gt; arr[i + 1] &gt; ... &gt; arr[arr.length - 1]</code></li>
	</ul>
	</li>
</ul>

<p>Given an integer array <code>nums</code>​​​, return <em>the <strong>minimum</strong> number of elements to remove to make </em><code>nums<em>​​​</em></code><em> </em><em>a <strong>mountain array</strong>.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> The array itself is a mountain array so we do not need to remove any elements.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,1,5,6,2,3,1]
<strong>Output:</strong> 3
<strong>Explanation:</strong> One solution is to remove the elements at indices 0, 1, and 5, making the array nums = [1,5,6,3,1].
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,3,2,1,1,2,3,1]
<strong>Output:</strong> 4
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,4,3,2,1]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li>It is guaranteed that you can make a mountain array out of <code>nums</code>.</li>
</ul>
 instead-->
<p>我们定义 <code>arr</code> 是 <b>山形数组</b> 当且仅当它满足：</p>

<ul>
	<li><code>arr.length &gt;= 3</code></li>
	<li>存在某个下标 <code>i</code> （<strong>从 0 开始</strong>） 满足 <code>0 &lt; i &lt; arr.length - 1</code> 且：
	<ul>
		<li><code>arr[0] &lt; arr[1] &lt; ... &lt; arr[i - 1] &lt; arr[i]</code></li>
		<li><code>arr[i] &gt; arr[i + 1] &gt; ... &gt; arr[arr.length - 1]</code></li>
	</ul>
	</li>
</ul>

<p>给你整数数组 <code>nums</code>​ ，请你返回将 <code>nums</code> 变成 <strong>山形状数组</strong> 的​ <strong>最少</strong> 删除次数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>nums = [1,3,1]
<b>输出：</b>0
<b>解释：</b>数组本身就是山形数组，所以我们不需要删除任何元素。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>nums = [2,1,1,5,6,2,3,1]
<b>输出：</b>3
<b>解释：</b>一种方法是将下标为 0，1 和 5 的元素删除，剩余元素为 [1,5,6,3,1] ，是山形数组。
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>nums = [4,3,2,1,1,2,3,1]
<b>输出：</b>4
</pre>

<p><strong>提示：</strong></p>

<pre><b>输入：</b>nums = [1,2,3,4,4,3,2,1]
<b>输出：</b>1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li>题目保证 <code>nums</code> 删除一些元素后一定能得到山形数组。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 50 ms

```java
class Solution {
    public int minimumMountainRemovals(int[] nums) {
        int[] dpl = new int[nums.length];
        int[] dpr = new int[nums.length];
        int max = 0;
        for (int i = 0; i < nums.length; i++) {
            if(i==0)
                continue;
            int l = i-1;
            for(int j = l;j>-1;j--){
                if(nums[i]>nums[j])
                dpl[i] = Math.max(dpl[i],dpl[j]+1);

            }
        }
        for (int i=nums.length-1;i>-1;i--){
            if(i==nums.length-1)
                continue;
            int r = i+1;
            for (int j = r;j<nums.length;j++){
                if(nums[i]>nums[j]){
                    dpr[i] = Math.max(dpr[i],dpr[j]+1);
                }

            }
        }
        for(int i=1;i<nums.length-1;i++){
            if(dpl[i]!=0&&dpr[i]!=0)
            max = Math.max(max,dpr[i]+dpl[i]+1);
        }
        return nums.length-max;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-number-of-removals-to-make-mountain-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-number-of-removals-to-make-mountain-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-number-of-removals-to-make-mountain-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-number-of-removals-to-make-mountain-array/)

[回到目录](../README.md)