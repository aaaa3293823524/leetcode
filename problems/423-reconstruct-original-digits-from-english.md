# 423. reconstruct-original-digits-from-english | 从英文中重建数字

## Question description

<!--If you want to use the English description, use <p>Given a <b>non-empty</b> string containing an out-of-order English representation of digits <code>0-9</code>, output the digits in ascending order.</p>

<p><b>Note:</b><br />
<ol>
<li>Input contains only lowercase English letters.</li>
<li>Input is guaranteed to be valid and can be transformed to its original digits. That means invalid inputs such as "abc" or "zerone" are not permitted.</li>
<li>Input length is less than 50,000.</li>
</ol>
</p>

<p><b>Example 1:</b><br />
<pre>
Input: "owoztneoer"

Output: "012"
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
Input: "fviefuro"

Output: "45"
</pre>
</p> instead-->
<p>给定一个<strong>非空</strong>字符串，其中包含字母顺序打乱的英文单词表示的数字<code>0-9</code>。按升序输出原始的数字。</p>

<p><strong>注意:</strong></p>

<ol>
	<li>输入只包含小写英文字母。</li>
	<li>输入保证合法并可以转换为原始的数字，这意味着像 &quot;abc&quot; 或 &quot;zerone&quot; 的输入是不允许的。</li>
	<li>输入字符串的长度小于 50,000。</li>
</ol>

<p><strong>示例 1:</strong></p>

<pre>
输入: &quot;owoztneoer&quot;

输出: &quot;012&quot; (zeroonetwo)
</pre>

<p><strong>示例 2:</strong></p>

<pre>
输入: &quot;fviefuro&quot;

输出: &quot;45&quot; (fourfive)
</pre>


## Note

哈希表


## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
  public String originalDigits(String s) {
    // building hashmap letter -> its frequency
    char[] count = new char[26 + (int)'a'];
    for(char letter: s.toCharArray()) {
      count[letter]++;
    }

    // building hashmap digit -> its frequency
    int[] out = new int[10];
    // letter "z" is present only in "zero"
    out[0] = count['z'];
    // letter "w" is present only in "two"
    out[2] = count['w'];
    // letter "u" is present only in "four"
    out[4] = count['u'];
    // letter "x" is present only in "six"
    out[6] = count['x'];
    // letter "g" is present only in "eight"
    out[8] = count['g'];
    // letter "h" is present only in "three" and "eight"
    out[3] = count['h'] - out[8];
    // letter "f" is present only in "five" and "four"
    out[5] = count['f'] - out[4];
    // letter "s" is present only in "seven" and "six"
    out[7] = count['s'] - out[6];
    // letter "i" is present in "nine", "five", "six", and "eight"
    out[9] = count['i'] - out[5] - out[6] - out[8];
    // letter "n" is present in "one", "nine", and "seven"
    out[1] = count['n'] - out[7] - 2 * out[9];

    // building output string
    StringBuilder output = new StringBuilder();
    for(int i = 0; i < 10; i++)
      for (int j = 0; j < out[i]; j++)
        output.append(i);
    return output.toString();
  }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reconstruct-original-digits-from-english/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reconstruct-original-digits-from-english/description/)

Solution: [LeetCode](https://leetcode.com/articles/reconstruct-original-digits-from-english/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reconstruct-original-digits-from-english/)

[回到目录](../README.md)