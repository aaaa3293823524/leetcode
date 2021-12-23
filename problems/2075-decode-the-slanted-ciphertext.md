# 2075. decode-the-slanted-ciphertext | 解码斜向换位密码

## Question description

<!--If you want to use the English description, use <p>A string <code>originalText</code> is encoded using a <strong>slanted transposition cipher</strong> to a string <code>encodedText</code> with the help of a matrix having a <strong>fixed number of rows</strong> <code>rows</code>.</p>

<p><code>originalText</code> is placed first in a top-left to bottom-right manner.</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/11/07/exa11.png" style="width: 300px; height: 185px;" />
<p>The blue cells are filled first, followed by the red cells, then the yellow cells, and so on, until we reach the end of <code>originalText</code>. The arrow indicates the order in which the cells are filled. All empty cells are filled with <code>&#39; &#39;</code>. The number of columns is chosen such that the rightmost column will <strong>not be empty</strong> after filling in <code>originalText</code>.</p>

<p><code>encodedText</code> is then formed by appending all characters of the matrix in a row-wise fashion.</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/11/07/exa12.png" style="width: 300px; height: 200px;" />
<p>The characters in the blue cells are appended first to <code>encodedText</code>, then the red cells, and so on, and finally the yellow cells. The arrow indicates the order in which the cells are accessed.</p>

<p>For example, if <code>originalText = &quot;cipher&quot;</code> and <code>rows = 3</code>, then we encode it in the following manner:</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/25/desc2.png" style="width: 281px; height: 211px;" />
<p>The blue arrows depict how <code>originalText</code> is placed in the matrix, and the red arrows denote the order in which <code>encodedText</code> is formed. In the above example, <code>encodedText = &quot;ch ie pr&quot;</code>.</p>

<p>Given the encoded string <code>encodedText</code> and number of rows <code>rows</code>, return <em>the original string</em> <code>originalText</code>.</p>

<p><strong>Note:</strong> <code>originalText</code> <strong>does not</strong> have any trailing spaces <code>&#39; &#39;</code>. The test cases are generated such that there is only one possible <code>originalText</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> encodedText = &quot;ch   ie   pr&quot;, rows = 3
<strong>Output:</strong> &quot;cipher&quot;
<strong>Explanation:</strong> This is the same example described in the problem description.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/26/exam1.png" style="width: 250px; height: 168px;" />
<pre>
<strong>Input:</strong> encodedText = &quot;iveo    eed   l te   olc&quot;, rows = 4
<strong>Output:</strong> &quot;i love leetcode&quot;
<strong>Explanation:</strong> The figure above denotes the matrix that was used to encode originalText. 
The blue arrows show how we can find originalText from encodedText.
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/26/eg2.png" style="width: 300px; height: 51px;" />
<pre>
<strong>Input:</strong> encodedText = &quot;coding&quot;, rows = 1
<strong>Output:</strong> &quot;coding&quot;
<strong>Explanation:</strong> Since there is only 1 row, both originalText and encodedText are the same.
</pre>

<p><strong>Example 4:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/26/exam3.png" style="width: 150px; height: 101px;" />
<pre>
<strong>Input:</strong> encodedText = &quot; b  ac&quot;, rows = 2
<strong>Output:</strong> &quot; abc&quot;
<strong>Explanation:</strong> originalText cannot have trailing spaces, but it may be preceded by one or more spaces.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= encodedText.length &lt;= 10<sup>6</sup></code></li>
	<li><code>encodedText</code> consists of lowercase English letters and <code>&#39; &#39;</code> only.</li>
	<li><code>encodedText</code> is a valid encoding of some <code>originalText</code> that <strong>does not</strong> have trailing spaces.</li>
	<li><code>1 &lt;= rows &lt;= 1000</code></li>
	<li>The testcases are generated such that there is <strong>only one</strong> possible <code>originalText</code>.</li>
</ul>
 instead-->
<p>字符串 <code>originalText</code> 使用 <strong>斜向换位密码</strong> ，经由 <strong>行数固定</strong> 为 <code>rows</code> 的矩阵辅助，加密得到一个字符串 <code>encodedText</code> 。</p>

<p><code>originalText</code> 先按从左上到右下的方式放置到矩阵中。</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/11/07/exa11.png" style="width: 300px; height: 185px;" />
<p>先填充蓝色单元格，接着是红色单元格，然后是黄色单元格，以此类推，直到到达 <code>originalText</code> 末尾。箭头指示顺序即为单元格填充顺序。所有空单元格用 <code>' '</code> 进行填充。矩阵的列数需满足：用 <code>originalText</code> 填充之后，最右侧列 <strong>不为空</strong> 。</p>

<p>接着按行将字符附加到矩阵中，构造&nbsp;<code>encodedText</code> 。</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/11/07/exa12.png" style="width: 300px; height: 200px;" />
<p>先把蓝色单元格中的字符附加到 <code>encodedText</code> 中，接着是红色单元格，最后是黄色单元格。箭头指示单元格访问顺序。</p>

<p>例如，如果 <code>originalText = "cipher"</code> 且 <code>rows = 3</code> ，那么我们可以按下述方法将其编码：</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/25/desc2.png" style="width: 281px; height: 211px;" />
<p>蓝色箭头标识 <code>originalText</code> 是如何放入矩阵中的，红色箭头标识形成 <code>encodedText</code> 的顺序。在上述例子中，<code>encodedText = "ch&nbsp; &nbsp;ie&nbsp; &nbsp;pr"</code> 。</p>

<p>给你编码后的字符串 <code>encodedText</code> 和矩阵的行数 <code>rows</code> ，返回源字符串 <code>originalText</code> 。</p>

<p><strong>注意：</strong><code>originalText</code> <strong>不</strong> 含任何尾随空格 <code>' '</code> 。生成的测试用例满足 <strong>仅存在一个</strong> 可能的 <code>originalText</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>encodedText = "ch   ie   pr", rows = 3
<strong>输出：</strong>"cipher"
<strong>解释：</strong>此示例与问题描述中的例子相同。
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/10/26/exam1.png" style="width: 250px; height: 168px;" /></p>

<pre>
<strong>输入：</strong>encodedText = "iveo    eed   l te   olc", rows = 4
<strong>输出：</strong>"i love leetcode"
<strong>解释：</strong>上图标识用于编码 originalText 的矩阵。 
蓝色箭头展示如何从 encodedText 找到 originalText 。
</pre>

<p><strong>示例 3：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/10/26/eg2.png" style="width: 300px; height: 51px;" /></p>

<pre>
<strong>输入：</strong>encodedText = "coding", rows = 1
<strong>输出：</strong>"coding"
<strong>解释：</strong>由于只有 1 行，所以 originalText 和 encodedText 是相同的。
</pre>

<p><strong>示例 4：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/26/exam3.png" style="width: 150px; height: 101px;" />
<pre>
<strong>输入：</strong>encodedText = " b  ac", rows = 2
<strong>输出：</strong>" abc"
<strong>解释：</strong>originalText 不能含尾随空格，但它可能会有一个或者多个前置空格。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= encodedText.length &lt;= 10<sup>6</sup></code></li>
	<li><code>encodedText</code> 仅由小写英文字母和 <code>' '</code> 组成</li>
	<li><code>encodedText</code> 是对某个 <strong>不含</strong> 尾随空格的 <code>originalText</code> 的一个有效编码</li>
	<li><code>1 &lt;= rows &lt;= 1000</code></li>
	<li>生成的测试用例满足 <strong>仅存在一个</strong> 可能的 <code>originalText</code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 76 ms

```cpp
class Solution {
public:
    string decodeCiphertext(string encodedText, int rows) {
        int cols = encodedText.size() / rows;   // 辅助矩阵的列数
        string res;   // 遍历到的字符
        for (int i = 0; i < cols; ++i){
            // 从左至右枚举每一条路径
            int r = 0;
            int c = i;
            while (r < rows && c < cols){
                res.push_back(encodedText[r*cols+c]);
                ++r;
                ++c;
            }
        }
        // 删去末尾空格
        while (res.size() and res.back() == ' '){
            res.pop_back();
        }
        return res;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/decode-the-slanted-ciphertext/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/decode-the-slanted-ciphertext/description/)

Solution: [LeetCode](https://leetcode.com/articles/decode-the-slanted-ciphertext/)  /  [LeetCode中国](https://leetcode-cn.com/articles/decode-the-slanted-ciphertext/)

[回到目录](../README.md)