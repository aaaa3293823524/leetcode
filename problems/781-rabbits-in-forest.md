# 781. rabbits-in-forest | 森林中的兔子

## Question description

<!--If you want to use the English description, use <p>There is a forest with an unknown number of rabbits. We asked n rabbits <strong>&quot;How many rabbits have the same color as you?&quot;</strong> and collected the answers in an integer array <code>answers</code> where <code>answers[i]</code> is the answer of the <code>i<sup>th</sup></code> rabbit.</p>

<p>Given the array <code>answers</code>, return <em>the minimum number of rabbits that could be in the forest</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> answers = [1,1,2]
<strong>Output:</strong> 5
<strong>Explanation:</strong>
The two rabbits that answered &quot;1&quot; could both be the same color, say red.
The rabbit that answered &quot;2&quot; can&#39;t be red or the answers would be inconsistent.
Say the rabbit that answered &quot;2&quot; was blue.
Then there should be 2 other blue rabbits in the forest that didn&#39;t answer into the array.
The smallest possible number of rabbits in the forest is therefore 5: 3 that answered plus 2 that didn&#39;t.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> answers = [10,10,10]
<strong>Output:</strong> 11
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= answers.length &lt;= 1000</code></li>
	<li><code>0 &lt;= answers[i] &lt; 1000</code></li>
</ul>
 instead-->
<p>森林中有未知数量的兔子。提问其中若干只兔子<strong> "还有多少只兔子与你（指被提问的兔子）颜色相同?"</strong> ，将答案收集到一个整数数组 <code>answers</code> 中，其中 <code>answers[i]</code> 是第 <code>i</code> 只兔子的回答。</p>

<p>给你数组 <code>answers</code> ，返回森林中兔子的最少数量。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>answers = [1,1,2]
<strong>输出：</strong>5
<strong>解释：</strong>
两只回答了 "1" 的兔子可能有相同的颜色，设为红色。 
之后回答了 "2" 的兔子不会是红色，否则他们的回答会相互矛盾。
设回答了 "2" 的兔子为蓝色。 
此外，森林中还应有另外 2 只蓝色兔子的回答没有包含在数组中。 
因此森林中兔子的最少数量是 5 只：3 只回答的和 2 只没有回答的。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>answers = [10,10,10]
<strong>输出：</strong>11
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= answers.length &lt;= 1000</code></li>
	<li><code>0 &lt;= answers[i] &lt; 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int numRabbits(int[] answers) {
         Arrays.sort(answers);
         int sum=0;
         HashMap<Integer, Integer>map=new HashMap<Integer, Integer>();
         for(int i=0;i<answers.length;i++) {
             //if(answers[i]==0)continue;
             if(map.getOrDefault(answers[i], 0)==0)map.put(answers[i], answers[i]);
             else {
                 map.put(answers[i],map.get(answers[i])-1);
             }
         }
         for(int t:map.values()) {
             sum+=t;
         }
        return sum+answers.length;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/rabbits-in-forest/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/rabbits-in-forest/description/)

Solution: [LeetCode](https://leetcode.com/articles/rabbits-in-forest/)  /  [LeetCode中国](https://leetcode-cn.com/articles/rabbits-in-forest/)

[回到目录](../README.md)