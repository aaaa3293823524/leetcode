# 8. string-to-integer-atoi | 字符串转换整数 (atoi)

## Question description

<!--If you want to use the English description, use <p>Implement the <code>myAtoi(string s)</code> function, which converts a string to a 32-bit signed integer (similar to C/C++&#39;s <code>atoi</code> function).</p>

<p>The algorithm for <code>myAtoi(string s)</code> is as follows:</p>

<ol>
	<li>Read in and ignore any leading whitespace.</li>
	<li>Check if the next character (if not already at the end of the string) is <code>&#39;-&#39;</code> or <code>&#39;+&#39;</code>. Read this character in if it is either. This determines if the final result is negative or positive respectively. Assume the result is positive if neither is present.</li>
	<li>Read in next the characters until the next non-digit character or the end of the input is reached. The rest of the string is ignored.</li>
	<li>Convert these digits into an integer (i.e. <code>&quot;123&quot; -&gt; 123</code>, <code>&quot;0032&quot; -&gt; 32</code>). If no digits were read, then the integer is <code>0</code>. Change the sign as necessary (from step 2).</li>
	<li>If the integer is out of the 32-bit signed integer range <code>[-2<sup>31</sup>, 2<sup>31</sup> - 1]</code>, then clamp the integer so that it remains in the range. Specifically, integers less than <code>-2<sup>31</sup></code> should be clamped to <code>-2<sup>31</sup></code>, and integers greater than <code>2<sup>31</sup> - 1</code> should be clamped to <code>2<sup>31</sup> - 1</code>.</li>
	<li>Return the integer as the final result.</li>
</ol>

<p><strong>Note:</strong></p>

<ul>
	<li>Only the space character <code>&#39; &#39;</code> is considered a whitespace character.</li>
	<li><strong>Do not ignore</strong> any characters other than the leading whitespace or the rest of the string after the digits.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;42&quot;
<strong>Output:</strong> 42
<strong>Explanation:</strong> The underlined characters are what is read in, the caret is the current reader position.
Step 1: &quot;42&quot; (no characters read because there is no leading whitespace)
         ^
Step 2: &quot;42&quot; (no characters read because there is neither a &#39;-&#39; nor &#39;+&#39;)
         ^
Step 3: &quot;<u>42</u>&quot; (&quot;42&quot; is read in)
           ^
The parsed integer is 42.
Since 42 is in the range [-2<sup>31</sup>, 2<sup>31</sup> - 1], the final result is 42.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;   -42&quot;
<strong>Output:</strong> -42
<strong>Explanation:</strong>
Step 1: &quot;<u>   </u>-42&quot; (leading whitespace is read and ignored)
            ^
Step 2: &quot;   <u>-</u>42&quot; (&#39;-&#39; is read, so the result should be negative)
             ^
Step 3: &quot;   -<u>42</u>&quot; (&quot;42&quot; is read in)
               ^
The parsed integer is -42.
Since -42 is in the range [-2<sup>31</sup>, 2<sup>31</sup> - 1], the final result is -42.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;4193 with words&quot;
<strong>Output:</strong> 4193
<strong>Explanation:</strong>
Step 1: &quot;4193 with words&quot; (no characters read because there is no leading whitespace)
         ^
Step 2: &quot;4193 with words&quot; (no characters read because there is neither a &#39;-&#39; nor &#39;+&#39;)
         ^
Step 3: &quot;<u>4193</u> with words&quot; (&quot;4193&quot; is read in; reading stops because the next character is a non-digit)
             ^
The parsed integer is 4193.
Since 4193 is in the range [-2<sup>31</sup>, 2<sup>31</sup> - 1], the final result is 4193.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 200</code></li>
	<li><code>s</code> consists of English letters (lower-case and upper-case), digits (<code>0-9</code>), <code>&#39; &#39;</code>, <code>&#39;+&#39;</code>, <code>&#39;-&#39;</code>, and <code>&#39;.&#39;</code>.</li>
</ul>
 instead-->
<p>请你来实现一个 <code>myAtoi(string s)</code> 函数，使其能将字符串转换成一个 32 位有符号整数（类似 C/C++ 中的 <code>atoi</code> 函数）。</p>

<p>函数 <code>myAtoi(string s)</code> 的算法如下：</p>

<ul>
	<li>读入字符串并丢弃无用的前导空格</li>
	<li>检查下一个字符（假设还未到字符末尾）为正还是负号，读取该字符（如果有）。 确定最终结果是负数还是正数。 如果两者都不存在，则假定结果为正。</li>
	<li>读入下一个字符，直到到达下一个非数字字符或到达输入的结尾。字符串的其余部分将被忽略。</li>
	<li>将前面步骤读入的这些数字转换为整数（即，"123" -> 123， "0032" -> 32）。如果没有读入数字，则整数为 <code>0</code> 。必要时更改符号（从步骤 2 开始）。</li>
	<li>如果整数数超过 32 位有符号整数范围 <code>[−2<sup>31</sup>,  2<sup>31 </sup>− 1]</code> ，需要截断这个整数，使其保持在这个范围内。具体来说，小于 <code>−2<sup>31</sup></code> 的整数应该被固定为 <code>−2<sup>31</sup></code> ，大于 <code>2<sup>31 </sup>− 1</code> 的整数应该被固定为 <code>2<sup>31 </sup>− 1</code> 。</li>
	<li>返回整数作为最终结果。</li>
</ul>

<p><strong>注意：</strong></p>

<ul>
	<li>本题中的空白字符只包括空格字符 <code>' '</code> 。</li>
	<li>除前导空格或数字后的其余字符串外，<strong>请勿忽略</strong> 任何其他字符。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "42"
<strong>输出：</strong>42
<strong>解释：</strong>加粗的字符串为已经读入的字符，插入符号是当前读取的字符。
第 1 步："42"（当前没有读入字符，因为没有前导空格）
         ^
第 2 步："42"（当前没有读入字符，因为这里不存在 '-' 或者 '+'）
         ^
第 3 步："<strong>42</strong>"（读入 "42"）
           ^
解析得到整数 42 。
由于 "42" 在范围 [-2<sup>31</sup>, 2<sup>31</sup> - 1] 内，最终结果为 42 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "   -42"
<strong>输出：</strong>-42
<strong>解释：</strong>
第 1 步："<strong>   </strong>-42"（读入前导空格，但忽视掉）
            ^
第 2 步："   <strong>-</strong>42"（读入 '-' 字符，所以结果应该是负数）
             ^
第 3 步："   -<strong>42</strong>"（读入 "42"）
               ^
解析得到整数 -42 。
由于 "-42" 在范围 [-2<sup>31</sup>, 2<sup>31</sup> - 1] 内，最终结果为 -42 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "4193 with words"
<strong>输出：</strong>4193
<strong>解释：</strong>
第 1 步："4193 with words"（当前没有读入字符，因为没有前导空格）
         ^
第 2 步："4193 with words"（当前没有读入字符，因为这里不存在 '-' 或者 '+'）
         ^
第 3 步："<strong>4193</strong> with words"（读入 "4193"；由于下一个字符不是一个数字，所以读入停止）
             ^
解析得到整数 4193 。
由于 "4193" 在范围 [-2<sup>31</sup>, 2<sup>31</sup> - 1] 内，最终结果为 4193 。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>s = "words and 987"
<strong>输出：</strong>0
<strong>解释：</strong>
第 1 步："words and 987"（当前没有读入字符，因为没有前导空格）
         ^
第 2 步："words and 987"（当前没有读入字符，因为这里不存在 '-' 或者 '+'）
         ^
第 3 步："words and 987"（由于当前字符 'w' 不是一个数字，所以读入停止）
         ^
解析得到整数 0 ，因为没有读入任何数字。
由于 0 在范围 [-2<sup>31</sup>, 2<sup>31</sup> - 1] 内，最终结果为 0 。</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>s = "-91283472332"
<strong>输出：</strong>-2147483648
<strong>解释：</strong>
第 1 步："-91283472332"（当前没有读入字符，因为没有前导空格）
         ^
第 2 步："<strong>-</strong>91283472332"（读入 '-' 字符，所以结果应该是负数）
          ^
第 3 步："-<strong>91283472332</strong>"（读入 "91283472332"）
                     ^
解析得到整数 -91283472332 。
由于 -91283472332 小于范围 [-2<sup>31</sup>, 2<sup>31</sup> - 1] 的下界，最终结果被截断为 -2<sup>31</sup> = -2147483648 。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= s.length <= 200</code></li>
	<li><code>s</code> 由英文字母（大写和小写）、数字（<code>0-9</code>）、<code>' '</code>、<code>'+'</code>、<code>'-'</code> 和 <code>'.'</code> 组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public int myAtoi(String str) {
        Automaton automaton = new Automaton();
        int length = str.length();
        for (int i = 0; i < length; ++i) {
            automaton.get(str.charAt(i));
        }
        return (int) (automaton.sign * automaton.ans);
    }
}

class Automaton {
    public int sign = 1;
    public long ans = 0;
    private String state = "start";
    private Map<String, String[]> table = new HashMap<String, String[]>() {{
        put("start", new String[]{"start", "signed", "in_number", "end"});
        put("signed", new String[]{"end", "end", "in_number", "end"});
        put("in_number", new String[]{"end", "end", "in_number", "end"});
        put("end", new String[]{"end", "end", "end", "end"});
    }};

    public void get(char c) {
        state = table.get(state)[get_col(c)];
        if ("in_number".equals(state)) {
            ans = ans * 10 + c - '0';
            ans = sign == 1 ? Math.min(ans, (long) Integer.MAX_VALUE) : Math.min(ans, -(long) Integer.MIN_VALUE);
        } else if ("signed".equals(state)) {
            sign = c == '+' ? 1 : -1;
        }
    }

    private int get_col(char c) {
        if (c == ' ') {
            return 0;
        }
        if (c == '+' || c == '-') {
            return 1;
        }
        if (Character.isDigit(c)) {
            return 2;
        }
        return 3;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/string-to-integer-atoi/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/string-to-integer-atoi/description/)

Solution: [LeetCode](https://leetcode.com/articles/string-to-integer-atoi/)  /  [LeetCode中国](https://leetcode-cn.com/articles/string-to-integer-atoi/)

[回到目录](../README.md)