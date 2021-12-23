# 989. add-to-array-form-of-integer | 数组形式的整数加法

## Question description

<!--If you want to use the English description, use <p>The <strong>array-form</strong> of an integer <code>num</code> is an array representing its digits in left to right order.</p>

<ul>
	<li>For example, for <code>num = 1321</code>, the array form is <code>[1,3,2,1]</code>.</li>
</ul>

<p>Given <code>num</code>, the <strong>array-form</strong> of an integer, and an integer <code>k</code>, return <em>the <strong>array-form</strong> of the integer</em> <code>num + k</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = [1,2,0,0], k = 34
<strong>Output:</strong> [1,2,3,4]
<strong>Explanation:</strong> 1200 + 34 = 1234
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = [2,7,4], k = 181
<strong>Output:</strong> [4,5,5]
<strong>Explanation:</strong> 274 + 181 = 455
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> num = [2,1,5], k = 806
<strong>Output:</strong> [1,0,2,1]
<strong>Explanation:</strong> 215 + 806 = 1021
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= num[i] &lt;= 9</code></li>
	<li><code>num</code> does not contain any leading zeros except for the zero itself.</li>
	<li><code>1 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>对于非负整数&nbsp;<code>X</code>&nbsp;而言，<em><code>X</code></em>&nbsp;的<em>数组形式</em>是每位数字按从左到右的顺序形成的数组。例如，如果&nbsp;<code>X = 1231</code>，那么其数组形式为&nbsp;<code>[1,2,3,1]</code>。</p>

<p>给定非负整数 <code>X</code> 的数组形式&nbsp;<code>A</code>，返回整数&nbsp;<code>X+K</code>&nbsp;的数组形式。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = [1,2,0,0], K = 34
<strong>输出：</strong>[1,2,3,4]
<strong>解释：</strong>1200 + 34 = 1234
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = [2,7,4], K = 181
<strong>输出：</strong>[4,5,5]
<strong>解释：</strong>274 + 181 = 455
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>A = [2,1,5], K = 806
<strong>输出：</strong>[1,0,2,1]
<strong>解释：</strong>215 + 806 = 1021
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>A = [9,9,9,9,9,9,9,9,9,9], K = 1
<strong>输出：</strong>[1,0,0,0,0,0,0,0,0,0,0]
<strong>解释：</strong>9999999999 + 1 = 10000000000
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 10000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 9</code></li>
	<li><code>0 &lt;= K &lt;= 10000</code></li>
	<li>如果&nbsp;<code>A.length &gt; 1</code>，那么&nbsp;<code>A[0] != 0</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 16 ms

```java
class Solution {
    public List<Integer> addToArrayForm(int[] A, int K) {
        int N = A.length;
        int cur = K;
        List<Integer> ans = new ArrayList();

        int i = N;
        while (--i >= 0 || cur > 0) {
            if (i >= 0)
                cur += A[i];
            ans.add(cur % 10);
            cur /= 10;
        }

        Collections.reverse(ans);
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-to-array-form-of-integer/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-to-array-form-of-integer/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-to-array-form-of-integer/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-to-array-form-of-integer/)

[回到目录](../README.md)