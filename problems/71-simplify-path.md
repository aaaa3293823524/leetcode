# 71. simplify-path | 简化路径

## Question description

<!--If you want to use the English description, use <p>Given a string <code>path</code>, which is an <strong>absolute path</strong> (starting with a slash <code>&#39;/&#39;</code>) to a file or directory in a Unix-style file system, convert it to the simplified <strong>canonical path</strong>.</p>

<p>In a Unix-style file system, a period <code>&#39;.&#39;</code> refers to the current directory, a double period <code>&#39;..&#39;</code> refers to the directory up a level, and any multiple consecutive slashes (i.e. <code>&#39;//&#39;</code>) are treated as a single slash <code>&#39;/&#39;</code>. For this problem, any other format of periods such as <code>&#39;...&#39;</code> are treated as file/directory names.</p>

<p>The <strong>canonical path</strong> should have the following format:</p>

<ul>
	<li>The path starts with a single slash <code>&#39;/&#39;</code>.</li>
	<li>Any two directories are separated by a single slash <code>&#39;/&#39;</code>.</li>
	<li>The path does not end with a trailing <code>&#39;/&#39;</code>.</li>
	<li>The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period <code>&#39;.&#39;</code> or double period <code>&#39;..&#39;</code>)</li>
</ul>

<p>Return <em>the simplified <strong>canonical path</strong></em>.</p>

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
<strong>Explanation:</strong> In the canonical path, multiple consecutive slashes are replaced by a single one.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= path.length &lt;= 3000</code></li>
	<li><code>path</code> consists of English letters, digits, period <code>&#39;.&#39;</code>, slash <code>&#39;/&#39;</code> or <code>&#39;_&#39;</code>.</li>
	<li><code>path</code> is a valid absolute Unix path.</li>
</ul>
 instead-->
<p>给你一个字符串 <code>path</code> ，表示指向某一文件或目录的 Unix 风格 <strong>绝对路径 </strong>（以 <code>'/'</code> 开头），请你将其转化为更加简洁的规范路径。</p>

<p class="MachineTrans-lang-zh-CN">在 Unix 风格的文件系统中，一个点（<code>.</code>）表示当前目录本身；此外，两个点 （<code>..</code>） 表示将目录切换到上一级（指向父目录）；两者都可以是复杂相对路径的组成部分。任意多个连续的斜杠（即，<code>'//'</code>）都被视为单个斜杠 <code>'/'</code> 。 对于此问题，任何其他格式的点（例如，<code>'...'</code>）均被视为文件/目录名称。</p>

<p>请注意，返回的 <strong>规范路径</strong> 必须遵循下述格式：</p>

<ul>
	<li>始终以斜杠 <code>'/'</code> 开头。</li>
	<li>两个目录名之间必须只有一个斜杠 <code>'/'</code> 。</li>
	<li>最后一个目录名（如果存在）<strong>不能 </strong>以 <code>'/'</code> 结尾。</li>
	<li>此外，路径仅包含从根目录到目标文件或目录的路径上的目录（即，不含 <code>'.'</code> 或 <code>'..'</code>）。</li>
</ul>

<p>返回简化后得到的 <strong>规范路径</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>path = "/home/"
<strong>输出：</strong>"/home"
<strong>解释：</strong>注意，最后一个目录名后面没有斜杠。 </pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>path = "/../"
<strong>输出：</strong>"/"
<strong>解释：</strong>从根目录向上一级是不可行的，因为根目录是你可以到达的最高级。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>path = "/home//foo/"
<strong>输出：</strong>"/home/foo"
<strong>解释：</strong>在规范路径中，多个连续斜杠需要用一个斜杠替换。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>path = "/a/./b/../../c/"
<strong>输出：</strong>"/c"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= path.length <= 3000</code></li>
	<li><code>path</code> 由英文字母，数字，<code>'.'</code>，<code>'/'</code> 或 <code>'_'</code> 组成。</li>
	<li><code>path</code> 是一个有效的 Unix 风格绝对路径。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public String simplifyPath(String path) {
        Stack<String> stack = new Stack<>();
        StringBuilder ret = new StringBuilder();
        for (String p : path.split("/")) {
            if (!stack.empty() && p.equals("..")) {
                stack.pop();
            } else if (!" ..".contains(p)) {
                stack.push(p);
            }
        }
        for (String i : stack) {
            ret.append("/" + i);
        }
        return ret.length() == 0 ? "/" : ret.toString();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/simplify-path/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/simplify-path/description/)

Solution: [LeetCode](https://leetcode.com/articles/simplify-path/)  /  [LeetCode中国](https://leetcode-cn.com/articles/simplify-path/)

[回到目录](../README.md)