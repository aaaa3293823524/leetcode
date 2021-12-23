# 168. excel-sheet-column-title | Excel表列名称

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>columnNumber</code>, return <em>its corresponding column title as it appears in an Excel sheet</em>.</p>

<p>For example:</p>

<pre>
A -&gt; 1
B -&gt; 2
C -&gt; 3
...
Z -&gt; 26
AA -&gt; 27
AB -&gt; 28 
...
</pre>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> columnNumber = 1
<strong>Output:</strong> &quot;A&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> columnNumber = 28
<strong>Output:</strong> &quot;AB&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> columnNumber = 701
<strong>Output:</strong> &quot;ZY&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= columnNumber &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给你一个整数 <code>columnNumber</code> ，返回它在 Excel 表中相对应的列名称。</p>

<p>例如：</p>

<pre>
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...
</pre>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>columnNumber = 1
<strong>输出：</strong>"A"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>columnNumber = 28
<strong>输出：</strong>"AB"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>columnNumber = 701
<strong>输出：</strong>"ZY"
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>columnNumber = 2147483647
<strong>输出：</strong>"FXSHRXW"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= columnNumber <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    string convertToTitle(int n) {
        string ret;
        while (n)
        {
            int k = n % 26;
            if (k == 0)
            {
                ret = 'Z' + ret;
                n -= 26;
            }
            else{
                char prev = 'A'+(k-1);
                ret = prev + ret;
            }
            n /= 26;
        }
        return ret;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/excel-sheet-column-title/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/excel-sheet-column-title/description/)

Solution: [LeetCode](https://leetcode.com/articles/excel-sheet-column-title/)  /  [LeetCode中国](https://leetcode-cn.com/articles/excel-sheet-column-title/)

[回到目录](../README.md)