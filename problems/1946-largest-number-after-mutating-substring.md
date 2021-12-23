# 1946. largest-number-after-mutating-substring | 子字符串突变后可能得到的最大整数

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>num</code>, which represents a large integer. You are also given a <strong>0-indexed</strong> integer array <code>change</code> of length <code>10</code> that maps each digit <code>0-9</code> to another digit. More formally, digit <code>d</code> maps to digit <code>change[d]</code>.</p>

<p>You may <strong>choose</strong> to <b>mutate a single substring</b> of <code>num</code>. To mutate a substring, replace each digit <code>num[i]</code> with the digit it maps to in <code>change</code> (i.e. replace <code>num[i]</code> with <code>change[num[i]]</code>).</p>

<p>Return <em>a string representing the <strong>largest</strong> possible integer after <strong>mutating</strong> (or choosing not to) a <strong>single substring</strong> of </em><code>num</code>.</p>

<p>A <strong>substring</strong> is a contiguous sequence of characters within the string.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;<u>1</u>32&quot;, change = [9,8,5,0,3,6,4,2,6,8]
<strong>Output:</strong> &quot;<u>8</u>32&quot;
<strong>Explanation:</strong> Replace the substring &quot;1&quot;:
- 1 maps to change[1] = 8.
Thus, &quot;<u>1</u>32&quot; becomes &quot;<u>8</u>32&quot;.
&quot;832&quot; is the largest number that can be created, so return it.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;<u>021</u>&quot;, change = [9,4,3,5,7,2,1,9,0,6]
<strong>Output:</strong> &quot;<u>934</u>&quot;
<strong>Explanation:</strong> Replace the substring &quot;021&quot;:
- 0 maps to change[0] = 9.
- 2 maps to change[2] = 3.
- 1 maps to change[1] = 4.
Thus, &quot;<u>021</u>&quot; becomes &quot;<u>934</u>&quot;.
&quot;934&quot; is the largest number that can be created, so return it.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;5&quot;, change = [1,4,7,5,3,2,5,6,9,4]
<strong>Output:</strong> &quot;5&quot;
<strong>Explanation:</strong> &quot;5&quot; is already the largest number that can be created, so return it.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num.length &lt;= 10<sup>5</sup></code></li>
	<li><code>num</code> consists of only digits <code>0-9</code>.</li>
	<li><code>change.length == 10</code></li>
	<li><code>0 &lt;= change[d] &lt;= 9</code></li>
</ul>
 instead-->
<p>给你一个字符串 <code>num</code> ，该字符串表示一个大整数。另给你一个长度为 <code>10</code> 且 <strong>下标从 0&nbsp; 开始</strong> 的整数数组 <code>change</code> ，该数组将 <code>0-9</code> 中的每个数字映射到另一个数字。更规范的说法是，数字 <code>d</code> 映射为数字 <code>change[d]</code> 。</p>

<p>你可以选择 <strong>突变</strong>&nbsp; <code>num</code> 的任一子字符串。<strong>突变</strong> 子字符串意味着将每位数字 <code>num[i]</code> 替换为该数字在 <code>change</code> 中的映射（也就是说，将 <code>num[i]</code> 替换为 <code>change[num[i]]</code>）。</p>

<p>请你找出在对 <code>num</code> 的任一子字符串执行突变操作（也可以不执行）后，可能得到的 <strong>最大整数</strong> ，并用字符串表示返回。</p>

<p><strong>子字符串</strong> 是字符串中的一个连续序列。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>num = "<strong><em>1</em></strong>32", change = [9,8,5,0,3,6,4,2,6,8]
<strong>输出：</strong>"<strong><em>8</em></strong>32"
<strong>解释：</strong>替换子字符串 "1"：
- 1 映射为 change[1] = 8 。
因此 "<strong><em>1</em></strong>32" 变为 "<strong><em>8</em></strong>32" 。
"832" 是可以构造的最大整数，所以返回它的字符串表示。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>num = "<strong><em>021</em></strong>", change = [9,4,3,5,7,2,1,9,0,6]
<strong>输出：</strong>"<strong><em>934</em></strong>"
<strong>解释：</strong>替换子字符串 "021"：
- 0 映射为 change[0] = 9 。
- 2 映射为 change[2] = 3 。
- 1 映射为 change[1] = 4 。
因此，"<strong><em>021</em></strong>" 变为 "<strong><em>934</em></strong>" 。
"934" 是可以构造的最大整数，所以返回它的字符串表示。 
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>num = "5", change = [1,4,7,5,3,2,5,6,9,4]
<strong>输出：</strong>"5"
<strong>解释：</strong>"5" 已经是可以构造的最大整数，所以返回它的字符串表示。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num.length &lt;= 10<sup>5</sup></code></li>
	<li><code>num</code> 仅由数字 <code>0-9</code> 组成</li>
	<li><code>change.length == 10</code></li>
	<li><code>0 &lt;= change[d] &lt;= 9</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1070 ms

```java
class Solution {
    public String maximumNumber(String num, int[] change) {
        HashMap<Integer, Integer>map=new HashMap<Integer, Integer>();
        for(int i=0;i<change.length;i++) {
            if(change[i]>=i)map.put(i,change[i]);
        }
        StringBuilder stringBuilder=new StringBuilder();
        int t=0;

        StringBuilder stringBuilder1=new StringBuilder();
        for(int i=0;i<num.length();i++){
            System.out.println(change[Integer.valueOf(num.charAt(i)-'0')]+"  "+Integer.valueOf(num.charAt(i)-'0'));
            if(change[Integer.valueOf(num.charAt(i)-'0')]<=Integer.valueOf(num.charAt(i)-'0')){t++;
                    stringBuilder1.append(Integer.valueOf(num.charAt(i)-'0'));
            }else{
                break;
            }
        }
        System.out.println("t:"+t);
        for(int i=t;i<num.length();i++) {
            System.out.println(Integer.valueOf(num.charAt(i)-'0'));
            if(map.containsKey(Integer.valueOf(num.charAt(i)-'0'))) {
                stringBuilder.append(change[Integer.valueOf(num.charAt(i)-'0')]);
                System.out.println("change:"+change[Integer.valueOf(num.charAt(i)-'0')]);
                if(i==num.length()-1)return stringBuilder1.toString()+stringBuilder.toString();
            }else {
                return stringBuilder1.toString()+stringBuilder.toString()+num.substring(i);
                //break;
            }
        }
        return num;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-number-after-mutating-substring/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-number-after-mutating-substring/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-number-after-mutating-substring/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-number-after-mutating-substring/)

[回到目录](../README.md)