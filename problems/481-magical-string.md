# 481. magical-string | 神奇字符串

## Question description

<!--If you want to use the English description, use <p>A magical string <code>s</code> consists of only <code>&#39;1&#39;</code> and <code>&#39;2&#39;</code> and obeys the following rules:</p>

<ul>
	<li>The string s is magical because concatenating the number of contiguous occurrences of characters <code>&#39;1&#39;</code> and <code>&#39;2&#39;</code> generates the string <code>s</code> itself.</li>
</ul>

<p>The first few elements of <code>s</code> is <code>s = &quot;1221121221221121122&hellip;&hellip;&quot;</code>. If we group the consecutive <code>1</code>&#39;s and <code>2</code>&#39;s in <code>s</code>, it will be <code>&quot;1 22 11 2 1 22 1 22 11 2 11 22 ......&quot;</code> and the occurrences of <code>1</code>&#39;s or <code>2</code>&#39;s in each group are <code>&quot;1 2 2 1 1 2 1 2 2 1 2 2 ......&quot;</code>. You can see that the occurrence sequence is <code>s</code> itself.</p>

<p>Given an integer <code>n</code>, return the number of <code>1</code>&#39;s in the first <code>n</code> number in the magical string <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 6
<strong>Output:</strong> 3
<strong>Explanation:</strong> The first 6 elements of magical string s is &quot;122112&quot; and it contains three 1&#39;s, so return 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>神奇字符串 <code>s</code> 仅由 <code>'1'</code> 和 <code>'2'</code> 组成，并需要遵守下面的规则：</p>

<ul>
	<li>神奇字符串 s 的神奇之处在于，串联字符串中 <code>'1'</code> 和 <code>'2'</code> 的连续出现次数可以生成该字符串。</li>
</ul>

<p><code>s</code> 的前几个元素是 <code>s = "1221121221221121122……"</code> 。如果将 <code>s</code> 中连续的若干 <code>1</code> 和 <code>2</code> 进行分组，可以得到 <code>"1 22 11 2 1 22 1 22 11 2 11 22 ......"</code> 。每组中 <code>1</code> 或者 <code>2</code> 的出现次数分别是 <code>"1 2 2 1 1 2 1 2 2 1 2 2 ......"</code> 。上面的出现次数正是 <code>s</code> 自身。</p>

<p>给你一个整数 <code>n</code> ，返回在神奇字符串 <code>s</code> 的前 <code>n</code> 个数字中 <code>1</code> 的数目。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 6
<strong>输出：</strong>3
<strong>解释：</strong>神奇字符串 s 的前 6 个元素是 “<code>122112</code>”，它包含三个 1，因此返回 3 。 
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int magicalString(int n) {
        boolean[] magic=new boolean[n];
        magic[0]=true;
        int count=0;
        int inx=0;
        for(int i=1;i<n;i++){
            //出现次数为1时，说明当前位置元素与前一位置不相同
            if(magic[inx]){
                magic[i]=true^magic[i-1];
            //出现次数为2时，当前位置元素与前一位置元素相同，并与后一位不同
            }else{
                magic[i]=magic[i-1];
                //如果存在后一位，则该位应与当前位不同
                i++;
                if(i<n) magic[i]=true^magic[i-1];
            }
            //更新指示个数的元素所在指针
            inx++;
        }
        //统计1出现的次数
        for(boolean flag:magic){
            if(flag) count++;
        }
        return count;

    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/magical-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/magical-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/magical-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/magical-string/)

[回到目录](../README.md)