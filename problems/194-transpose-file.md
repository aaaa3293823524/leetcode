# 194. transpose-file | 转置文件

## Question description

<!--If you want to use the English description, use <p>Given a text file <code>file.txt</code>, transpose its content.</p>

<p>You may assume that each row has the same number of columns, and each field is separated by the <code>&#39; &#39;</code> character.</p>

<p><strong>Example:</strong></p>

<p>If <code>file.txt</code> has the following content:</p>

<pre>
name age
alice 21
ryan 30
</pre>

<p>Output the following:</p>

<pre>
name alice ryan
age 21 30
</pre>
 instead-->
<p>给定一个文件 <code>file.txt</code>，转置它的内容。</p>

<p>你可以假设每行列数相同，并且每个字段由 <code>' '</code> 分隔。</p>

<p> </p>

<p><strong>示例：</strong></p>

<p>假设 <code>file.txt</code> 文件内容如下：</p>

<pre>
name age
alice 21
ryan 30
</pre>

<p>应当输出：</p>

<pre>
name alice ryan
age 21 30
</pre>




## Solution

Language: **bash**  /  Runtime: 24 ms

```bash
# Read from the file file.txt and print its transposed content to stdout.

#!/bin/bash
line=`cat file.txt|awk '{print NF}'|head -n 1`
for n in $(seq 1 ${line});
do

   cat  file.txt |awk -v n=$n '{print $n}' |xargs echo 

done



```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/transpose-file/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/transpose-file/description/)

Solution: [LeetCode](https://leetcode.com/articles/transpose-file/)  /  [LeetCode中国](https://leetcode-cn.com/articles/transpose-file/)

[回到目录](../README.md)