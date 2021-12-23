# 1187. make-array-strictly-increasing | 使数组严格递增

## Question description

<!--If you want to use the English description, use <p>Given two integer arrays&nbsp;<code>arr1</code> and <code>arr2</code>, return the minimum number of operations (possibly zero) needed&nbsp;to make <code>arr1</code> strictly increasing.</p>

<p>In one operation, you can choose two indices&nbsp;<code>0 &lt;=&nbsp;i &lt; arr1.length</code>&nbsp;and&nbsp;<code>0 &lt;= j &lt; arr2.length</code>&nbsp;and do the assignment&nbsp;<code>arr1[i] = arr2[j]</code>.</p>

<p>If there is no way to make&nbsp;<code>arr1</code>&nbsp;strictly increasing,&nbsp;return&nbsp;<code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr1 = [1,5,3,6,7], arr2 = [1,3,2,4]
<strong>Output:</strong> 1
<strong>Explanation:</strong> Replace <code>5</code> with <code>2</code>, then <code>arr1 = [1, 2, 3, 6, 7]</code>.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr1 = [1,5,3,6,7], arr2 = [4,3,1]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Replace <code>5</code> with <code>3</code> and then replace <code>3</code> with <code>4</code>. <code>arr1 = [1, 3, 4, 6, 7]</code>.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr1 = [1,5,3,6,7], arr2 = [1,6,3,3]
<strong>Output:</strong> -1
<strong>Explanation:</strong> You can&#39;t make <code>arr1</code> strictly increasing.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr1.length, arr2.length &lt;= 2000</code></li>
	<li><code>0 &lt;= arr1[i], arr2[i] &lt;= 10^9</code></li>
</ul>

<p>&nbsp;</p> instead-->
<p>给你两个整数数组&nbsp;<code>arr1</code> 和 <code>arr2</code>，返回使&nbsp;<code>arr1</code>&nbsp;严格递增所需要的最小「操作」数（可能为 0）。</p>

<p>每一步「操作」中，你可以分别从 <code>arr1</code> 和 <code>arr2</code> 中各选出一个索引，分别为&nbsp;<code>i</code> 和&nbsp;<code>j</code>，<code>0 &lt;=&nbsp;i &lt; arr1.length</code>&nbsp;和&nbsp;<code>0 &lt;= j &lt; arr2.length</code>，然后进行赋值运算&nbsp;<code>arr1[i] = arr2[j]</code>。</p>

<p>如果无法让&nbsp;<code>arr1</code>&nbsp;严格递增，请返回&nbsp;<code>-1</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>arr1 = [1,5,3,6,7], arr2 = [1,3,2,4]
<strong>输出：</strong>1
<strong>解释：</strong>用 2 来替换 <code>5，之后</code> <code>arr1 = [1, 2, 3, 6, 7]</code>。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>arr1 = [1,5,3,6,7], arr2 = [4,3,1]
<strong>输出：</strong>2
<strong>解释：</strong>用 3 来替换 <code>5，然后</code>用 4 来替换 3<code>，得到</code> <code>arr1 = [1, 3, 4, 6, 7]</code>。
</pre>

<p><strong>示例&nbsp;3：</strong></p>

<pre><strong>输入：</strong>arr1 = [1,5,3,6,7], arr2 = [1,6,3,3]
<strong>输出：</strong>-1
<strong>解释：</strong>无法使 <code>arr1 严格递增</code>。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= arr1.length, arr2.length &lt;= 2000</code></li>
	<li><code>0 &lt;= arr1[i], arr2[i] &lt;= 10^9</code></li>
</ul>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 16 ms

```java
class Solution {
    public int makeArrayIncreasing(int[] arr1, int[] arr2) {
        List<Integer> arr1List = Arrays.stream(arr1).boxed().collect(Collectors.toList());
        arr1List.add(0,-1);
        arr1List.add(Integer.MAX_VALUE);
        arr1 = arr1List.stream().mapToInt(i -> i).toArray();

        arr2 = Arrays.stream(arr2).distinct().sorted().toArray();

        int[] dp = new int[arr1.length];
        Arrays.fill(dp,Integer.MAX_VALUE);
        dp[0] = 0; dp[1] = 0;
        for(int i=2; i<arr1.length; i++){
            int cost = 0, j = i-1;
            int current = arr1[j], next = arr1[i], arr2Index = arr2.length-1;

            for(int start = 0; start<arr2Index;){
                int mid = (start + arr2Index + 1) / 2;

                if(arr2[mid] >= next) arr2Index = mid -1;
                else start = mid;
            }
            if(arr2[arr2Index] >= next) arr2Index = -1;

            while (true){
                if(current < next && dp[j] != Integer.MAX_VALUE) dp[i] = Math.min(dp[i], dp[j] + cost);

                while (arr2Index >= 0 && arr2[arr2Index] >= next) arr2Index--;
                if(arr2Index < 0) break;

                cost++;
                if(--j < 0) break;

                next = arr2[arr2Index];
                current = arr1[j];
            }

            if(arr1[i-1] < arr1[i]) dp[i] = Math.min(dp[i], dp[i-1]);
        }

        return dp[arr1.length-1] != Integer.MAX_VALUE ? dp[arr1.length-1] : -1;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/make-array-strictly-increasing/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/make-array-strictly-increasing/description/)

Solution: [LeetCode](https://leetcode.com/articles/make-array-strictly-increasing/)  /  [LeetCode中国](https://leetcode-cn.com/articles/make-array-strictly-increasing/)

[回到目录](../README.md)