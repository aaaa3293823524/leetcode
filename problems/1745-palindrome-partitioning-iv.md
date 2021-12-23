# 1745. palindrome-partitioning-iv | 回文串分割 IV

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, return <code>true</code> <em>if it is possible to split the string</em> <code>s</code> <em>into three <strong>non-empty</strong> palindromic substrings. Otherwise, return </em><code>false</code>.​​​​​</p>

<p>A string is said to be palindrome if it the same string when reversed.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcbdd&quot;
<strong>Output:</strong> true
<strong>Explanation: </strong>&quot;abcbdd&quot; = &quot;a&quot; + &quot;bcb&quot; + &quot;dd&quot;, and all three substrings are palindromes.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bcbddxy&quot;
<strong>Output:</strong> false
<strong>Explanation: </strong>s cannot be split into 3 palindromes.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code>​​​​​​ consists only of lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个字符串 <code>s</code> ，如果可以将它分割成三个 <strong>非空</strong> 回文子字符串，那么返回 <code>true</code> ，否则返回 <code>false</code> 。</p>

<p>当一个字符串正着读和反着读是一模一样的，就称其为 <strong>回文字符串</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>s = "abcbdd"
<b>输出：</b>true
<strong>解释：</strong>"abcbdd" = "a" + "bcb" + "dd"，三个子字符串都是回文的。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>s = "bcbddxy"
<b>输出：</b>false
<strong>解释：</strong>s 没办法被分割成 3 个回文子字符串。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 <= s.length <= 2000</code></li>
	<li><code>s</code>​​​​​​ 只包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 9 ms

```java
class Solution {
    public boolean checkPartitioning(String s) {
        int n = s.length();
        int[] p = manacher(s); //manacher算法线性得到所有回文串

        TreeSet<Integer> leftSet = new TreeSet<>(); //左侧所有的前缀回文
        TreeSet<Integer> rightSet = new TreeSet<>(); //右侧所有的后缀回文
        for (int i = 0; i < p.length; i++) {
            if (i - p[i] == -1 && i + p[i] >= 2) { //通过@hqztrue大佬提示，发现还要判断大于2
                leftSet.add(i + p[i] - 2 >> 1);
            }

            if (i + p[i] == p.length) {
                rightSet.add(i - p[i] + 2 >> 1);
            }
        }

        int[] leftDp = new int[s.length()]; //每位往右但不到最后一位的最长回文
        for (int i = 0; i < leftDp.length; i++) {
            leftDp[i] = i;
        }

        int i1 = leftDp.length - 1;
        int i2 = p.length - 1;
        while (i1 >= 0) {
            while (i1 > 0 && i1 * 2 + 1 > i2) {
                i1--;
            }
            int indexI1 = i1 * 2 + 1;
            while (i2 > 0 && (indexI1 < i2 - p[i2] + 1 || i2 * 2 - indexI1 >= p.length - 2)) {
                i2--;
            }

            if (indexI1 >= i2 - p[i2] + 1 && indexI1 <= i2) {
                leftDp[i1] = Math.max(leftDp[i1], i2 * 2 - indexI1 >> 1);
                i1--;
            }
        }

        for (int x : leftSet) {
            if (checked(x + 1, n - 1, leftDp, rightSet, p)) { //对每个左侧确定的回文，检查右边是不是能由两个非空回文组成
                return true;
            }
        }
        return false;
    }

    private boolean checked(int i, int end, int[] leftDp, TreeSet<Integer> rightSet, int[] p) {
        if (i >= end) {
            return false;
        }

        //left Max，左侧取最长回文前缀，判断右边剩下的是不是回文。
        int j = leftDp[i];
        int center = j + 1 + end + 1;
        if (p[center] > end - j) {
            return true;
        }

        //right Max，右侧取最长回文后缀，判断左边剩下的是不是回文
        int k = rightSet.ceiling(i + 1);
        int center2 = i + k - 1 + 1;
        if (p[center2] > k - i) {
            return true;
        }

        return false;
    }

    /**
    * manacher算法
    **/
    public int[] manacher(String s) {
        int[] p = new int[(s.length() << 1) + 1];
        int rightBound = -1;
        int center = -1;

        char[] stringChars = s.toCharArray();

        for (int i = 0; i < p.length; i++) {
            p[i] = i < rightBound ? Math.min(p[(center << 1) - i], rightBound - i + 1) : 1;
            while (i - p[i] > -1 && i + p[i] < p.length && (((i + p[i] & 0x1) == 0) || stringChars[i + p[i] >> 1] == stringChars[i - p[i] >> 1])) {
                p[i]++;
            }

            if (i + p[i] - 1 > rightBound) {
                rightBound = i + p[i] - 1;
                center = i;
            }
        }

        return p;
    }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/palindrome-partitioning-iv/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/palindrome-partitioning-iv/description/)

Solution: [LeetCode](https://leetcode.com/articles/palindrome-partitioning-iv/)  /  [LeetCode中国](https://leetcode-cn.com/articles/palindrome-partitioning-iv/)

[回到目录](../README.md)