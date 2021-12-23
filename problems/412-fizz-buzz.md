# 412. fizz-buzz | Fizz Buzz

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>n</code>, return <em>a string array </em><code>answer</code><em> (<strong>1-indexed</strong>) where</em>:</p>

<ul>
	<li><code>answer[i] == &quot;FizzBuzz&quot;</code> if <code>i</code> is divisible by <code>3</code> and <code>5</code>.</li>
	<li><code>answer[i] == &quot;Fizz&quot;</code> if <code>i</code> is divisible by <code>3</code>.</li>
	<li><code>answer[i] == &quot;Buzz&quot;</code> if <code>i</code> is divisible by <code>5</code>.</li>
	<li><code>answer[i] == i</code> (as a string) if none of the above conditions are true.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> ["1","2","Fizz"]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> n = 5
<strong>Output:</strong> ["1","2","Fizz","4","Buzz"]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> n = 15
<strong>Output:</strong> ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个整数 <code>n</code> ，找出从 <code>1</code> 到 <code>n</code> 各个整数的 Fizz Buzz 表示，并用字符串数组 <code>answer</code>（<strong>下标从 1 开始</strong>）返回结果，其中：</p>

<ul>
	<li><code>answer[i] == "FizzBuzz"</code> 如果 <code>i</code> 同时是 <code>3</code> 和 <code>5</code> 的倍数。</li>
	<li><code>answer[i] == "Fizz"</code> 如果 <code>i</code> 是 <code>3</code> 的倍数。</li>
	<li><code>answer[i] == "Buzz"</code> 如果 <code>i</code> 是 <code>5</code> 的倍数。</li>
	<li><code>answer[i] == i</code> （以字符串形式）如果上述条件全不满足。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>["1","2","Fizz"]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 5
<strong>输出：</strong>["1","2","Fizz","4","Buzz"]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>n = 15
<strong>输出：</strong>["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String>list=new ArrayList<String>();
        for(int i=1;i<=n;i++) {
            if(i%3==0&&i%5==0)list.add("FizzBuzz");
            else if(i%3==0&&i%5!=0)list.add("Fizz");
            else if(i%3!=0&&i%5==0)list.add("Buzz");
            else {
                list.add(i+"");
            }
        }
        return list;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/fizz-buzz/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fizz-buzz/description/)

Solution: [LeetCode](https://leetcode.com/articles/fizz-buzz/)  /  [LeetCode中国](https://leetcode-cn.com/articles/fizz-buzz/)

[回到目录](../README.md)