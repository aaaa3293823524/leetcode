# 1397. find-all-good-strings | 找到所有好字符串

## Question description

<!--If you want to use the English description, use <p>Given the strings <code>s1</code> and <code>s2</code> of size <code>n</code> and the string <code>evil</code>, return <em>the number of <strong>good</strong> strings</em>.</p>

<p>A <strong>good</strong> string has size <code>n</code>, it is alphabetically greater than or equal to <code>s1</code>, it is alphabetically smaller than or equal to <code>s2</code>, and it does not contain the string <code>evil</code> as a substring. Since the answer can be a huge number, return this <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 2, s1 = &quot;aa&quot;, s2 = &quot;da&quot;, evil = &quot;b&quot;
<strong>Output:</strong> 51 
<strong>Explanation:</strong> There are 25 good strings starting with &#39;a&#39;: &quot;aa&quot;,&quot;ac&quot;,&quot;ad&quot;,...,&quot;az&quot;. Then there are 25 good strings starting with &#39;c&#39;: &quot;ca&quot;,&quot;cc&quot;,&quot;cd&quot;,...,&quot;cz&quot; and finally there is one good string starting with &#39;d&#39;: &quot;da&quot;.&nbsp;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 8, s1 = &quot;leetcode&quot;, s2 = &quot;leetgoes&quot;, evil = &quot;leet&quot;
<strong>Output:</strong> 0 
<strong>Explanation:</strong> All strings greater than or equal to s1 and smaller than or equal to s2 start with the prefix &quot;leet&quot;, therefore, there is not any good string.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 2, s1 = &quot;gx&quot;, s2 = &quot;gz&quot;, evil = &quot;x&quot;
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>s1.length == n</code></li>
	<li><code>s2.length == n</code></li>
	<li><code>s1 &lt;= s2</code></li>
	<li><code>1 &lt;= n &lt;= 500</code></li>
	<li><code>1 &lt;= evil.length &lt;= 50</code></li>
	<li>All strings consist of lowercase English letters.</li>
</ul>
 instead-->
<p>给你两个长度为 <code>n</code>&nbsp;的字符串&nbsp;<code>s1</code> 和&nbsp;<code>s2</code>&nbsp;，以及一个字符串&nbsp;<code>evil</code>&nbsp;。请你返回 <strong>好字符串&nbsp;</strong>的数目。</p>

<p><strong>好字符串</strong>&nbsp;的定义为：它的长度为&nbsp;<code>n</code>&nbsp;，字典序大于等于&nbsp;<code>s1</code>&nbsp;，字典序小于等于&nbsp;<code>s2</code>&nbsp;，且不包含&nbsp;<code>evil</code>&nbsp;为子字符串。</p>

<p>由于答案可能很大，请你返回答案对 10^9 + 7 取余的结果。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 2, s1 = &quot;aa&quot;, s2 = &quot;da&quot;, evil = &quot;b&quot;
<strong>输出：</strong>51 
<strong>解释：</strong>总共有 25 个以 &#39;a&#39; 开头的好字符串：&quot;aa&quot;，&quot;ac&quot;，&quot;ad&quot;，...，&quot;az&quot;。还有 25 个以 &#39;c&#39; 开头的好字符串：&quot;ca&quot;，&quot;cc&quot;，&quot;cd&quot;，...，&quot;cz&quot;。最后，还有一个以 &#39;d&#39; 开头的好字符串：&quot;da&quot;。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>n = 8, s1 = &quot;leetcode&quot;, s2 = &quot;leetgoes&quot;, evil = &quot;leet&quot;
<strong>输出：</strong>0 
<strong>解释：</strong>所有字典序大于等于 s1 且小于等于 s2 的字符串都以 evil 字符串 &quot;leet&quot; 开头。所以没有好字符串。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>n = 2, s1 = &quot;gx&quot;, s2 = &quot;gz&quot;, evil = &quot;x&quot;
<strong>输出：</strong>2
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>s1.length == n</code></li>
	<li><code>s2.length == n</code></li>
	<li><code>s1 &lt;= s2</code></li>
	<li><code>1 &lt;= n &lt;= 500</code></li>
	<li><code>1 &lt;= evil.length &lt;= 50</code></li>
	<li>所有字符串都只包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 24 ms

```java
class Solution {
    int[] fail;
    // 这是存储动态规划结果的数组
    // 维度从左到右分别为 pos, stats, bound
    int[][][] f;
    // int f[500][50][4];
    // 这是存储转移函数结果的数组
    // 两个维度分别为 stats 和 d
    int[][] trans;
    static final int MOD = 1000000007;
    String s1, s2, evil;

    public int findGoodStrings(int n, String s1, String s2, String evil) {
        this.s1 = s1;
        this.s2 = s2;
        this.evil = evil;

        int m = evil.length();
        fail = new int[m];
        // 这是 KMP 算法的一部分
        // 把「evil」看作模式串，得到它的 fail[] 数组
        for (int i = 1; i < m; ++i) {
            int j = fail[i - 1];
            while (j != 0 && evil.charAt(j) != evil.charAt(i)) {
                j = fail[j - 1];
            }
            if (evil.charAt(j) == evil.charAt(i)) {
                fail[i] = j + 1;
            }
        }
        // 将未搜索过的动态规划状态置为 -1
        f = new int[n][m][4];
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < m; ++j) {
                Arrays.fill(f[i][j], -1);
            }
        }
        // 将未计算过的转移函数置为 -1
        trans = new int[m][26];
        for (int i = 0; i < m; ++i) {
            Arrays.fill(trans[i], -1);
        }
        // 答案即为 f[0][0][3]
        return dfs(0, 0, 3);
    }

    // 这是用来进行记忆化搜索的函数
    // 输入为 pos, stats 和 bound
    // 输出为 f[pos][stats][bound]
    public int dfs(int pos, int stats, int bound) {
        // 如果匹配到了 evil 的末尾
        // 说明字符串不满足要求了
        // 返回 0
        if (stats == evil.length()) {
            return 0;
        }
        // 如果匹配到了上下界的末尾
        // 说明找到了一个满足要求的字符串
        // 返回 1
        if (pos == s1.length()) {
            return 1;
        }
        // 记忆化搜索的关键
        // 如果之前计算过该状态就直接返回结果
        if (f[pos][stats][bound] != -1) {
            return f[pos][stats][bound];
        }
        
        // 将当前状态初始化
        // 因为未初始化的状态值为 -1
        f[pos][stats][bound] = 0;
        // 计算第 pos 位可枚举的字符下界
        char l = ((bound & 1) != 0 ? s1.charAt(pos) : 'a');
        // 计算第 pos 位可枚举的字符上界
        char r = ((bound & 2) != 0 ? s2.charAt(pos) : 'z');
        for (char ch = l; ch <= r; ++ch) {
            int nxt_stats = getTrans(stats, ch);
            // 这里写得较为复杂
            // 本质上就是关于 bound 的转移函数
            // 可以根据自己的理解编写
            int nxt_bound = ((bound & 1) != 0 ? (ch == s1.charAt(pos) ? 1 : 0) : 0) ^ ((bound & 2) != 0 ? (ch == s2.charAt(pos) ? 1 : 0) << 1 : 0);
            f[pos][stats][bound] += dfs(pos + 1, nxt_stats, nxt_bound);
            f[pos][stats][bound] %= MOD;
        }
        return f[pos][stats][bound];
    }

    // 这是计算关于 stats 的转移函数
    // 输入为 stats 和 d
    // 输出为转移的结果 g_s(stats, d)
    public int getTrans(int stats, char ch) {
        // 如果之前计算过该转移函数就直接返回结果
        if (trans[stats][ch - 'a'] != -1) {
            return trans[stats][ch - 'a'];
        }
        // 这是 KMP 算法的一部分
        // 把 evil 看作「模式串」，stats 看作「主串」匹配到的位置
        while (stats != 0 && evil.charAt(stats) != ch) {
            stats = fail[stats - 1];
        }
        // 存储结果并返回
        return trans[stats][ch - 'a'] = (evil.charAt(stats) == ch ? stats + 1 : 0);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-all-good-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-all-good-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-all-good-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-all-good-strings/)

[回到目录](../README.md)