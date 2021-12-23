# 805. split-array-with-same-average | 数组的均值分割

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>nums</code>.</p>

<p>You should move each element of <code>nums</code> into one of the two arrays <code>A</code> and <code>B</code> such that <code>A</code> and <code>B</code> are non-empty, and <code>average(A) == average(B)</code>.</p>

<p>Return <code>true</code> if it is possible to achieve that and <code>false</code> otherwise.</p>

<p><strong>Note</strong> that for an array <code>arr</code>, <code>average(arr)</code> is the sum of all the elements of <code>arr</code> over the length of <code>arr</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5,6,7,8]
<strong>Output:</strong> true
<strong>Explanation:</strong> We can split the array into [1,4,5,8] and [2,3,6,7], and both of them have an average of 4.5.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,1]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 30</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给定的整数数组 A ，我们要将 A数组 中的每个元素移动到 B数组 或者 C数组中。（B数组和C数组在开始的时候都为空）</p>

<p>返回<code>true</code> ，当且仅当在我们的完成这样的移动后，可使得B数组的平均值和C数组的平均值相等，并且B数组和C数组都不为空。</p>

<pre>
<strong>示例:</strong>
<strong>输入:</strong> 
[1,2,3,4,5,6,7,8]
<strong>输出:</strong> true
<strong>解释: </strong>我们可以将数组分割为 [1,4,5,8] 和 [2,3,6,7], 他们的平均值都是4.5。
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>A</code> 数组的长度范围为 <code>[1, 30]</code>.</li>
	<li><code>A[i]</code> 的数据范围为 <code>[0, 10000]</code>.</li>
</ul>




## Solution

Language: **java**  /  Runtime: 703 ms

```java
class Solution {
    public boolean splitArraySameAverage(int[] nums) {
        int total = Arrays.stream(nums).sum();
        Set<Integer>[] dp = new HashSet[total + 1];
        dp[0] = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
            for (int j = total - 1; j >= nums[i]; j--) {
                if (dp[j - nums[i]] != null) {
                    if (dp[j] == null) {
                        dp[j] = new HashSet<>();
                    }
                    if (j == nums[i]) {
                        dp[j].add(1);
                    }
                    // 状态转移
                    List<Integer> list = new ArrayList<>();
                    for (int c : dp[j - nums[i]]) {
                        list.add(c + 1);
                    }
                    dp[j].addAll(list);

                    for (int c : dp[j]) {
                        if (c * total == j * nums.length) {
                            return true;
                        }
                    }
                }
            }
        }
        return false;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/split-array-with-same-average/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/split-array-with-same-average/description/)

Solution: [LeetCode](https://leetcode.com/articles/split-array-with-same-average/)  /  [LeetCode中国](https://leetcode-cn.com/articles/split-array-with-same-average/)

[回到目录](../README.md)