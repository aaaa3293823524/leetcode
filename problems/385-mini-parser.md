﻿# 385. mini-parser | 迷你语法分析器

## Question description

<!--If you want to use the English description, use <p>Given a string s represents the serialization of a nested list, implement a parser to deserialize it and return <em>the deserialized</em> <code>NestedInteger</code>.</p>

<p>Each element is either an integer or a list whose elements may also be integers or other lists.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;324&quot;
<strong>Output:</strong> 324
<strong>Explanation:</strong> You should return a NestedInteger object which contains a single integer 324.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;[123,[456,[789]]]&quot;
<strong>Output:</strong> [123,[456,[789]]]
<strong>Explanation:</strong> Return a NestedInteger object containing a nested list with 2 elements:
1. An integer containing value 123.
2. A nested list containing two elements:
    i.  An integer containing value 456.
    ii. A nested list with one element:
         a. An integer containing value 789
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> consists of digits, square brackets <code>&quot;[]&quot;</code>, negative sign <code>&#39;-&#39;</code>, and commas <code>&#39;,&#39;</code>.</li>
	<li><code>s</code> is the serialization of valid <code>NestedInteger</code>.</li>
	<li>All the values in the input are in the range <code>[-10<sup>6</sup>, 10<sup>6</sup>]</code>.</li>
</ul>
 instead-->
<p>给定一个用字符串表示的整数的嵌套列表，实现一个解析它的语法分析器。</p>

<p>列表中的每个元素只可能是整数或整数嵌套列表</p>

<p><strong>提示：</strong>你可以假定这些字符串都是格式良好的：</p>

<ul>
	<li>字符串非空</li>
	<li>字符串不包含空格</li>
	<li>字符串只包含数字<code>0-9</code>、<code>[</code>、<code>-</code>、<code>,</code>、<code>]</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>给定 s = &quot;324&quot;,

你应该返回一个 NestedInteger 对象，其中只包含整数值 324。
</pre>

<p><strong>示例 2：</strong></p>

<pre>给定 s = &quot;[123,[456,[789]]]&quot;,

返回一个 NestedInteger 对象包含一个有两个元素的嵌套列表：

1. 一个 integer 包含值 123
2. 一个包含两个元素的嵌套列表：
    i.  一个 integer 包含值 456
    ii. 一个包含一个元素的嵌套列表
         a. 一个 integer 包含值 789
</pre>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * public interface NestedInteger {
 *     // Constructor initializes an empty nested list.
 *     public NestedInteger();
 *
 *     // Constructor initializes a single integer.
 *     public NestedInteger(int value);
 *
 *     // @return true if this NestedInteger holds a single integer, rather than a nested list.
 *     public boolean isInteger();
 *
 *     // @return the single integer that this NestedInteger holds, if it holds a single integer
 *     // Return null if this NestedInteger holds a nested list
 *     public Integer getInteger();
 *
 *     // Set this NestedInteger to hold a single integer.
 *     public void setInteger(int value);
 *
 *     // Set this NestedInteger to hold a nested list and adds a nested integer to it.
 *     public void add(NestedInteger ni);
 *
 *     // @return the nested list that this NestedInteger holds, if it holds a nested list
 *     // Return empty list if this NestedInteger holds a single integer
 *     public List<NestedInteger> getList();
 * }
 */
class Solution {
    //递归函数通过字符数组和cur下标确定要处理的位置
    char[] chars;
    int cur = 0;
    public NestedInteger deserialize(String s) {
        chars = s.toCharArray();
        //本身不是一个集合而是一个整数的情况
        if(chars[0]!='[') return new NestedInteger(Integer.valueOf(s));
        //调用递归函数返回根集合
        return getNest();
    }
    public NestedInteger getNest(){
        NestedInteger nest = new NestedInteger();
        int num = 0;//num用于缓存用逗号分割的整数类型的值
        int sign = 1;//当前记录的整数的符号，1代表整数，-1代表负数
        while(cur!=chars.length-1){
            cur ++;
            if(chars[cur]==',') continue;
            if(chars[cur]=='[') nest.add(getNest());//遇到[递归获取子集合
            else if(chars[cur]==']') return nest;
            else if(chars[cur]=='-') sign = -1;
            else{//是数字的情况
                num = 10*num + sign * (chars[cur]-'0');
                //如果下一个字符是,或者]说明当前数字已经记录完了，需要加入集合中
                if(chars[cur+1]==','||chars[cur+1]==']'){ 
                    nest.add(new NestedInteger(num));
                    num = 0;
                    sign = 1;
                }
            }
        }
        return null;
    }
}




```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/mini-parser/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/mini-parser/description/)

Solution: [LeetCode](https://leetcode.com/articles/mini-parser/)  /  [LeetCode中国](https://leetcode-cn.com/articles/mini-parser/)

[回到目录](../README.md)