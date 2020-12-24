# 71. simplify-path | 简化路径

## Question description

<!--If you want to use the English description, use <p>Given an <strong>absolute path</strong> for a file (Unix-style), simplify it. Or in other words, convert it to the <strong>canonical path</strong>.</p>

<p>In a UNIX-style file system, a period <code>&#39;.&#39;</code>&nbsp;refers to the current directory. Furthermore, a double period <code>&#39;..&#39;</code>&nbsp;moves the directory up a level.</p>

<p>Note that the returned canonical path must always begin&nbsp;with a slash <code>&#39;/&#39;</code>, and there must be only a single slash <code>&#39;/&#39;</code>&nbsp;between two directory names.&nbsp;The last directory name (if it exists) <b>must not</b>&nbsp;end with a trailing <code>&#39;/&#39;</code>. Also, the canonical path must be the <strong>shortest</strong> string&nbsp;representing the absolute path.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> path = &quot;/home/&quot;
<strong>Output:</strong> &quot;/home&quot;
<strong>Explanation:</strong> Note that there is no trailing slash after the last directory name.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> path = &quot;/../&quot;
<strong>Output:</strong> &quot;/&quot;
<strong>Explanation:</strong> Going one level up from the root directory is a no-op, as the root level is the highest level you can go.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> path = &quot;/home//foo/&quot;
<strong>Output:</strong> &quot;/home/foo&quot;
<strong>Explanation: </strong>In the canonical path, multiple consecutive slashes are replaced by a single one.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> path = &quot;/a/./b/../../c/&quot;
<strong>Output:</strong> &quot;/c&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= path.length &lt;= 3000</code></li>
	<li><code>path</code> consists of English letters, digits, period <code>&#39;.&#39;</code>, slash <code>&#39;/&#39;</code> or <code>&#39;_&#39;</code>.</li>
	<li><code>path</code> is a valid Unix path.</li>
</ul>
 instead-->
<p>以 Unix 风格给出一个文件的<strong>绝对路径</strong>，你需要简化它。或者换句话说，将其转换为规范路径。</p>

<p>在 Unix 风格的文件系统中，一个点（<code>.</code>）表示当前目录本身；此外，两个点 （<code>..</code>）&nbsp;表示将目录切换到上一级（指向父目录）；两者都可以是复杂相对路径的组成部分。更多信息请参阅：<a href="https://blog.csdn.net/u011327334/article/details/50355600" target="_blank">Linux / Unix中的绝对路径 vs 相对路径</a></p>

<p>请注意，返回的规范路径必须始终以斜杠 <code>/</code> 开头，并且两个目录名之间必须只有一个斜杠 <code>/</code>。最后一个目录名（如果存在）<strong>不能</strong>以 <code>/</code> 结尾。此外，规范路径必须是表示绝对路径的<strong>最短</strong>字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：&quot;</strong>/home/&quot;
<strong>输出：&quot;</strong>/home&quot;
<strong>解释：</strong>注意，最后一个目录名后面没有斜杠。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：&quot;</strong>/../&quot;
<strong>输出：&quot;</strong>/&quot;
<strong>解释：</strong>从根目录向上一级是不可行的，因为根是你可以到达的最高级。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：&quot;</strong>/home//foo/&quot;
<strong>输出：&quot;</strong>/home/foo&quot;
<strong>解释：</strong>在规范路径中，多个连续斜杠需要用一个斜杠替换。
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：&quot;</strong>/a/./b/../../c/&quot;
<strong>输出：&quot;</strong>/c&quot;
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：&quot;</strong>/a/../../b/../c//.//&quot;
<strong>输出：&quot;</strong>/c&quot;
</pre>

<p><strong>示例 6：</strong></p>

<pre><strong>输入：&quot;</strong>/a//b////c/d//././/..&quot;
<strong>输出：&quot;</strong>/a/b/c&quot;</pre>




## Solution

Language: **java**  /  Runtime: 16 ms

```java
// 1.此题主要考察的是栈,所以定义一个辅助栈;
// 2.先把字符串以"/"为分隔符分割成数组,此时数组有"路径"、""、"."、".."这四种情况;
// 3.遍历数组,当s[i].equals("..")并且栈不空时pop,当!s[i].equals("") && !s[i].equals(".") && !s[i].equals(".."),即s[i]是路径入栈;
// 4.栈空,返回"/",栈非空,用StringBuffer做一个连接返回即可;

class Solution {
public String simplifyPath(String path) {
        String[] s = path.split("/");
        Stack<String> stack = new Stack<>();
        
        for (int i = 0; i < s.length; i++) {
            if (!stack.isEmpty() && s[i].equals(".."))
                stack.pop();
            else if (!s[i].equals("") && !s[i].equals(".") && !s[i].equals(".."))
                stack.push(s[i]);
        }
        if (stack.isEmpty())
            return "/";

        StringBuffer res = new StringBuffer();
        for (int i = 0; i < stack.size(); i++) {
            res.append("/" + stack.get(i));
        }
        return res.toString();
    }

}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/simplify-path/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/simplify-path/description/)

Solution: [LeetCode](https://leetcode.com/articles/simplify-path/)  /  [LeetCode中国](https://leetcode-cn.com/articles/simplify-path/)

[回到目录](../README.md)