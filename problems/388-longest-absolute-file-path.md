# 388. longest-absolute-file-path | 文件的最长绝对路径

## Question description

<!--If you want to use the English description, use <p>Suppose we have a file system that stores both files and directories. An example of one system is represented in the following picture:</p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/mdir.jpg" style="width: 681px; height: 322px;" /></p>

<p>Here, we have <code>dir</code> as the only directory in the root. <code>dir</code> contains two subdirectories, <code>subdir1</code> and <code>subdir2</code>. <code>subdir1</code> contains a file <code>file1.ext</code> and subdirectory <code>subsubdir1</code>. <code>subdir2</code> contains a subdirectory <code>subsubdir2</code>, which contains a file <code>file2.ext</code>.</p>

<p>In text form, it looks like this (with ⟶ representing the tab character):</p>

<pre>
dir
⟶ subdir1
⟶ ⟶ file1.ext
⟶ ⟶ subsubdir1
⟶ subdir2
⟶ ⟶ subsubdir2
⟶ ⟶ ⟶ file2.ext
</pre>

<p>If we were to write this representation in code, it will look like this: <code>&quot;dir\n\tsubdir1\n\t\tfile1.ext\n\t\tsubsubdir1\n\tsubdir2\n\t\tsubsubdir2\n\t\t\tfile2.ext&quot;</code>. Note that the <code>&#39;\n&#39;</code> and <code>&#39;\t&#39;</code> are the new-line and tab characters.</p>

<p>Every file and directory has a unique <strong>absolute path</strong> in the file system, which is the order of directories that must be opened to reach the file/directory itself, all concatenated by <code>&#39;/&#39;s</code>. Using the above example, the <strong>absolute path</strong> to <code>file2.ext</code> is <code>&quot;dir/subdir2/subsubdir2/file2.ext&quot;</code>. Each directory name consists of letters, digits, and/or spaces. Each file name is of the form <code>name.extension</code>, where <code>name</code> and <code>extension</code> consist of letters, digits, and/or spaces.</p>

<p>Given a string <code>input</code> representing the file system in the explained format, return <em>the length of the <strong>longest absolute path</strong> to a <strong>file</strong> in the abstracted file system</em>. If there is no file in the system, return <code>0</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/dir1.jpg" style="width: 401px; height: 202px;" />
<pre>
<strong>Input:</strong> input = &quot;dir\n\tsubdir1\n\tsubdir2\n\t\tfile.ext&quot;
<strong>Output:</strong> 20
<strong>Explanation:</strong> We have only one file, and the absolute path is &quot;dir/subdir2/file.ext&quot; of length 20.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/dir2.jpg" style="width: 641px; height: 322px;" />
<pre>
<strong>Input:</strong> input = &quot;dir\n\tsubdir1\n\t\tfile1.ext\n\t\tsubsubdir1\n\tsubdir2\n\t\tsubsubdir2\n\t\t\tfile2.ext&quot;
<strong>Output:</strong> 32
<strong>Explanation:</strong> We have two files:
&quot;dir/subdir1/file1.ext&quot; of length 21
&quot;dir/subdir2/subsubdir2/file2.ext&quot; of length 32.
We return 32 since it is the longest absolute path to a file.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> input = &quot;a&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> We do not have any files, just a single directory named &quot;a&quot;.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> input = &quot;file1.txt\nfile2.txt\nlongfile.txt&quot;
<strong>Output:</strong> 12
<strong>Explanation:</strong> There are 3 files at the root directory.
Since the absolute path for anything at the root directory is just the name itself, the answer is &quot;longfile.txt&quot; with length 12.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= input.length &lt;= 10<sup>4</sup></code></li>
	<li><code>input</code> may contain lowercase or uppercase English letters, a new line character <code>&#39;\n&#39;</code>, a tab character <code>&#39;\t&#39;</code>, a dot <code>&#39;.&#39;</code>, a space <code>&#39; &#39;</code>, and digits.</li>
</ul>
 instead-->
<p>假设有一个同时存储文件和目录的文件系统。下图展示了文件系统的一个示例：</p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/mdir.jpg" style="width: 681px; height: 322px;" /></p>

<p>这里将 <code>dir</code> 作为根目录中的唯一目录。<code>dir</code> 包含两个子目录 <code>subdir1</code> 和 <code>subdir2</code> 。<code>subdir1</code> 包含文件 <code>file1.ext</code> 和子目录 <code>subsubdir1</code>；<code>subdir2</code> 包含子目录 <code>subsubdir2</code>，该子目录下包含文件 <code>file2.ext</code> 。</p>

<p>在文本格式中，如下所示(⟶表示制表符)：</p>

<pre>
dir
⟶ subdir1
⟶ ⟶ file1.ext
⟶ ⟶ subsubdir1
⟶ subdir2
⟶ ⟶ subsubdir2
⟶ ⟶ ⟶ file2.ext
</pre>

<p>如果是代码表示，上面的文件系统可以写为 <code>"dir\n\tsubdir1\n\t\tfile1.ext\n\t\tsubsubdir1\n\tsubdir2\n\t\tsubsubdir2\n\t\t\tfile2.ext"</code> 。<code>'\n'</code> 和 <code>'\t'</code> 分别是换行符和制表符。</p>

<p>文件系统中的每个文件和文件夹都有一个唯一的 <strong>绝对路径</strong> ，即必须打开才能到达文件/目录所在位置的目录顺序，所有路径用 <code>'/'</code> 连接。上面例子中，指向 <code>file2.ext</code> 的绝对路径是 <code>"dir/subdir2/subsubdir2/file2.ext"</code> 。每个目录名由字母、数字和/或空格组成，每个文件名遵循 <code>name.extension</code> 的格式，其中名称和扩展名由字母、数字和/或空格组成。</p>

<p>给定一个以上述格式表示文件系统的字符串 <code>input</code> ，返回文件系统中 <strong>指向文件的最长绝对路径</strong> 的长度。 如果系统中没有文件，返回&nbsp;<code>0</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/dir1.jpg" style="width: 401px; height: 202px;" />
<pre>
<strong>输入：</strong>input = "dir\n\tsubdir1\n\tsubdir2\n\t\tfile.ext"
<strong>输出：</strong>20
<strong>解释：</strong>只有一个文件，绝对路径为 "dir/subdir2/file.ext" ，路径长度 20
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/dir2.jpg" style="width: 641px; height: 322px;" />
<pre>
<strong>输入：</strong>input = "dir\n\tsubdir1\n\t\tfile1.ext\n\t\tsubsubdir1\n\tsubdir2\n\t\tsubsubdir2\n\t\t\tfile2.ext"
<strong>输出：</strong>32
<strong>解释：</strong>存在两个文件：
"dir/subdir1/file1.ext" ，路径长度 21
"dir/subdir2/subsubdir2/file2.ext" ，路径长度 32
返回 32 ，因为这是最长的路径</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>input = "a"
<strong>输出：</strong>0
<strong>解释：</strong>不存在任何文件</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>input = "file1.txt\nfile2.txt\nlongfile.txt"
<strong>输出：</strong>12
<strong>解释：</strong>根目录下有 3 个文件。
因为根目录中任何东西的绝对路径只是名称本身，所以答案是 "longfile.txt" ，路径长度为 12
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= input.length &lt;= 10<sup>4</sup></code></li>
	<li><code>input</code> 可能包含小写或大写的英文字母，一个换行符 <code>'\n'</code>，一个制表符 <code>'\t'</code>，一个点 <code>'.'</code>，一个空格 <code>' '</code>，和数字。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int lengthLongestPath(String input) {
        Stack<Integer> stack = new Stack<>();
        stack.push(0);
        int ans = 0;
        // 以 \n 分割成字符串数组
        String[] str = input.split("\n");
        // dir,\tsubdir1,\tsubdir2,\tfile.ext
        for (String s : str) {
            // level 代表当前字符串的首字母索引
            // 字符串前面可能会有多个 \t,故使用 lastIndexOf 找出最后一个 \t 位置即可
            int level = s.lastIndexOf("\t") + 1;
            while (level + 1 < stack.size()) {
                stack.pop();
            }
            // 之前入栈的字符串 + 当前遍历到的字符串的长度
            int len = stack.peek() + (s.length() - level + 1);
            stack.push(len);
            if (s.contains(".")) {
                ans = Math.max(ans, len - 1);
            }
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-absolute-file-path/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-absolute-file-path/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-absolute-file-path/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-absolute-file-path/)

[回到目录](../README.md)