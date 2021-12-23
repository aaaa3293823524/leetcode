# 321. create-maximum-number | 拼接最大数

## Question description

<!--If you want to use the English description, use <p>You are given two integer arrays <code>nums1</code> and <code>nums2</code> of lengths <code>m</code> and <code>n</code> respectively. <code>nums1</code> and <code>nums2</code> represent the digits of two numbers. You are also given an integer <code>k</code>.</p>

<p>Create the maximum number of length <code>k &lt;= m + n</code> from digits of the two numbers. The relative order of the digits from the same array must be preserved.</p>

<p>Return an array of the <code>k</code> digits representing the answer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [3,4,6,5], nums2 = [9,1,2,5,8,3], k = 5
<strong>Output:</strong> [9,8,6,5,3]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [6,7], nums2 = [6,0,4], k = 5
<strong>Output:</strong> [6,7,6,0,4]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [3,9], nums2 = [8,9], k = 3
<strong>Output:</strong> [9,8,9]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == nums1.length</code></li>
	<li><code>n == nums2.length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>0 &lt;= nums1[i], nums2[i] &lt;= 9</code></li>
	<li><code>1 &lt;= k &lt;= m + n</code></li>
</ul>
 instead-->
<p>给定长度分别为&nbsp;<code>m</code>&nbsp;和&nbsp;<code>n</code>&nbsp;的两个数组，其元素由&nbsp;<code>0-9</code>&nbsp;构成，表示两个自然数各位上的数字。现在从这两个数组中选出 <code>k (k &lt;= m + n)</code>&nbsp;个数字拼接成一个新的数，要求从同一个数组中取出的数字保持其在原数组中的相对顺序。</p>

<p>求满足该条件的最大数。结果返回一个表示该最大数的长度为&nbsp;<code>k</code>&nbsp;的数组。</p>

<p><strong>说明: </strong>请尽可能地优化你算法的时间和空间复杂度。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
nums1 = <code>[3, 4, 6, 5]</code>
nums2 = <code>[9, 1, 2, 5, 8, 3]</code>
k = <code>5</code>
<strong>输出:</strong>
<code>[9, 8, 6, 5, 3]</code></pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong>
nums1 = <code>[6, 7]</code>
nums2 = <code>[6, 0, 4]</code>
k = <code>5</code>
<strong>输出:</strong>
<code>[6, 7, 6, 0, 4]</code></pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong>
nums1 = <code>[3, 9]</code>
nums2 = <code>[8, 9]</code>
k = <code>3</code>
<strong>输出:</strong>
<code>[9, 8, 9]</code></pre>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
class Solution {
    public int[] maxNumber(int[] nums1, int[] nums2, int k) {
        int m = nums1.length, n = nums2.length;
        int[] maxSubsequence = new int[k];
        int start = Math.max(0, k - n), end = Math.min(k, m);
        for (int i = start; i <= end; i++) {
            int[] subsequence1 = maxSubsequence(nums1, i);
            int[] subsequence2 = maxSubsequence(nums2, k - i);
            int[] curMaxSubsequence = merge(subsequence1, subsequence2);
            if (compare(curMaxSubsequence, 0, maxSubsequence, 0) > 0) {
                System.arraycopy(curMaxSubsequence, 0, maxSubsequence, 0, k);
            }
        }
        return maxSubsequence;
    }

    public int[] maxSubsequence(int[] nums, int k) {
        int length = nums.length;
        int[] stack = new int[k];
        int top = -1;
        int remain = length - k;
        for (int i = 0; i < length; i++) {
            int num = nums[i];
            while (top >= 0 && stack[top] < num && remain > 0) {
                top--;
                remain--;
            }
            if (top < k - 1) {
                stack[++top] = num;
            } else {
                remain--;
            }
        }
        return stack;
    }

    public int[] merge(int[] subsequence1, int[] subsequence2) {
        int x = subsequence1.length, y = subsequence2.length;
        if (x == 0) {
            return subsequence2;
        }
        if (y == 0) {
            return subsequence1;
        }
        int mergeLength = x + y;
        int[] merged = new int[mergeLength];
        int index1 = 0, index2 = 0;
        for (int i = 0; i < mergeLength; i++) {
            if (compare(subsequence1, index1, subsequence2, index2) > 0) {
                merged[i] = subsequence1[index1++];
            } else {
                merged[i] = subsequence2[index2++];
            }
        }
        return merged;
    }

    public int compare(int[] subsequence1, int index1, int[] subsequence2, int index2) {
        int x = subsequence1.length, y = subsequence2.length;
        while (index1 < x && index2 < y) {
            int difference = subsequence1[index1] - subsequence2[index2];
            if (difference != 0) {
                return difference;
            }
            index1++;
            index2++;
        }
        return (x - index1) - (y - index2);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/create-maximum-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/create-maximum-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/create-maximum-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/create-maximum-number/)

[回到目录](../README.md)