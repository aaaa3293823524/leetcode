# 2002. maximum-product-of-the-length-of-two-palindromic-subsequences | 两个回文子序列长度的最大乘积

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, find two <strong>disjoint palindromic subsequences</strong> of <code>s</code> such that the <strong>product</strong> of their lengths is <strong>maximized</strong>. The two subsequences are <strong>disjoint</strong> if they do not both pick a character at the same index.</p>

<p>Return <em>the <strong>maximum</strong> possible <strong>product</strong> of the lengths of the two palindromic subsequences</em>.</p>

<p>A <strong>subsequence</strong> is a string that can be derived from another string by deleting some or no characters without changing the order of the remaining characters. A string is <strong>palindromic</strong> if it reads the same forward and backward.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="example-1" src="https://assets.leetcode.com/uploads/2021/08/24/two-palindromic-subsequences.png" style="width: 550px; height: 124px;" />
<pre>
<strong>Input:</strong> s = &quot;leetcodecom&quot;
<strong>Output:</strong> 9
<strong>Explanation</strong>: An optimal solution is to choose &quot;ete&quot; for the 1<sup>st</sup> subsequence and &quot;cdc&quot; for the 2<sup>nd</sup> subsequence.
The product of their lengths is: 3 * 3 = 9.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bb&quot;
<strong>Output:</strong> 1
<strong>Explanation</strong>: An optimal solution is to choose &quot;b&quot; (the first character) for the 1<sup>st</sup> subsequence and &quot;b&quot; (the second character) for the 2<sup>nd</sup> subsequence.
The product of their lengths is: 1 * 1 = 1.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;accbcaxxcxx&quot;
<strong>Output:</strong> 25
<strong>Explanation</strong>: An optimal solution is to choose &quot;accca&quot; for the 1<sup>st</sup> subsequence and &quot;xxcxx&quot; for the 2<sup>nd</sup> subsequence.
The product of their lengths is: 5 * 5 = 25.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= s.length &lt;= 12</code></li>
	<li><code>s</code> consists of lowercase English letters only.</li>
</ul>
 instead-->
<p>给你一个字符串&nbsp;<code>s</code>&nbsp;，请你找到&nbsp;<code>s</code>&nbsp;中两个&nbsp;<strong>不相交回文子序列</strong>&nbsp;，使得它们长度的&nbsp;<strong>乘积最大</strong>&nbsp;。两个子序列在原字符串中如果没有任何相同下标的字符，则它们是&nbsp;<strong>不相交</strong>&nbsp;的。</p>

<p>请你返回两个回文子序列长度可以达到的<strong>&nbsp;最大乘积</strong>&nbsp;。</p>

<p><strong>子序列</strong>&nbsp;指的是从原字符串中删除若干个字符（可以一个也不删除）后，剩余字符不改变顺序而得到的结果。如果一个字符串从前往后读和从后往前读一模一样，那么这个字符串是一个 <strong>回文字符串</strong>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="example-1" src="https://assets.leetcode.com/uploads/2021/08/24/two-palindromic-subsequences.png" style="width: 550px; height: 124px;"></p>

<pre><b>输入：</b>s = "leetcodecom"
<b>输出：</b>9
<b>解释：</b>最优方案是选择 "ete" 作为第一个子序列，"cdc" 作为第二个子序列。
它们的乘积为 3 * 3 = 9 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>s = "bb"
<b>输出：</b>1
<b>解释：</b>最优方案为选择 "b" （第一个字符）作为第一个子序列，"b" （第二个字符）作为第二个子序列。
它们的乘积为 1 * 1 = 1 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>s = "accbcaxxcxx"
<b>输出：</b>25
<b>解释：</b>最优方案为选择 "accca" 作为第一个子序列，"xxcxx" 作为第二个子序列。
它们的乘积为 5 * 5 = 25 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= s.length &lt;= 12</code></li>
	<li><code>s</code>&nbsp;只含有小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 41 ms

```java
class Solution {
    private boolean check(char[] s, int state) {
        int left = 0, right = s.length - 1;
        
        // 检查 state 对应的子序列是不是回文串
        while (left < right) {
            // 将 left 和 right 对应上 「状态所对应的字符」 位置
            while (left < right && (state >> left & 1) == 0) {
                left++;
            }
            while (left < right && (state >> right & 1) == 0) {
                right--;
            }
            if (s[left] != s[right]) {
                return false;
            }
            left++;
            right--;
        }
        
        return true;
    }
    
    public int maxProduct(String s) {
        int n = s.length(), m = 1 << n;
        List<int[]> list = new ArrayList<>();
        var str = s.toCharArray();
        
        // 记录所有合法状态的信息
        for (int i = 1; i < m; i++) {
            if (check(str, i)) {
                list.add(new int[]{ i, Integer.bitCount(i) });
            }
        }
        
        int[][] arr = list.toArray(new int[0][0]);
        int res = 0, len = arr.length;
        // for-each 优化，j 不需要从 0 开始
        for (int i = 0; i < len; i++) {
            int x = arr[i][0], len_x = arr[i][1];
            for (int j = i + 1; j < len; j++) {
                int y = arr[j][0], len_y = arr[j][1];
                // 状态之间没有字符相交，满足题意
                if ((x & y) == 0) {
                    res = Math.max(res, len_x * len_y);
                }
            }
        }
        
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-product-of-the-length-of-two-palindromic-subsequences/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-product-of-the-length-of-two-palindromic-subsequences/)

[回到目录](../README.md)