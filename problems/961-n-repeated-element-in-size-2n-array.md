# 961. n-repeated-element-in-size-2n-array | 重复 N 次的元素

## Question description

<!--If you want to use the English description, use <p>In a array <code>A</code> of size <code>2N</code>, there are <code>N+1</code> unique elements, and exactly one of these elements is repeated <code>N</code> times.</p>

<p>Return the element repeated <code>N</code> times.</p>

<p>&nbsp;</p>

<ol>
</ol>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,2,3,3]</span>
<strong>Output: </strong><span id="example-output-1">3</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[2,1,2,5,3,2]</span>
<strong>Output: </strong><span id="example-output-2">2</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">[5,1,5,2,5,3,5,4]</span>
<strong>Output: </strong><span id="example-output-3">5</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ul>
	<li><code>4 &lt;= A.length &lt;= 10000</code></li>
	<li><code>0 &lt;= A[i] &lt; 10000</code></li>
	<li><code>A.length</code> is even</li>
</ul>
</div>
</div>
</div>
 instead-->
<p>在大小为 <code>2N</code>&nbsp;的数组 <code>A</code>&nbsp;中有 <code>N+1</code> 个不同的元素，其中有一个元素重复了 <code>N</code> 次。</p>

<p>返回重复了 <code>N</code>&nbsp;次的那个元素。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[1,2,3,3]
<strong>输出：</strong>3
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[2,1,2,5,3,2]
<strong>输出：</strong>2
</pre>

<p><strong>示例&nbsp;3：</strong></p>

<pre><strong>输入：</strong>[5,1,5,2,5,3,5,4]
<strong>输出：</strong>5
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>4 &lt;= A.length &lt;= 10000</code></li>
	<li><code>0 &lt;= A[i] &lt; 10000</code></li>
	<li><code>A.length</code>&nbsp;为偶数</li>
</ol>




## Solution

Language: **java**  /  Runtime: 54 ms

```java
class Solution {
    public static int repeatedNTimes(int[] A) {
        int len=A.length;
        HashMap<Integer, Integer>map=new HashMap<>();
        for(int i=0;i<len;i++) {
            if (!map.containsKey(A[i])) {
                map.put(A[i], 1);
            }else {
                map.put(A[i], map.get(A[i])+1);
            }
        }
        for(Map.Entry<Integer, Integer>entry:map.entrySet()) {
            if (entry.getValue()==len/2) {
                return entry.getKey();
            }
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/n-repeated-element-in-size-2n-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/n-repeated-element-in-size-2n-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/n-repeated-element-in-size-2n-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/n-repeated-element-in-size-2n-array/)

[回到目录](../README.md)