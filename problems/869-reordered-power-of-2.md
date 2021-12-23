# 869. reordered-power-of-2 | 重新排序得到 2 的幂

## Question description

<!--If you want to use the English description, use <p>You are given an integer <code>n</code>. We reorder the digits in any order (including the original order) such that the leading digit is not zero.</p>

<p>Return <code>true</code> <em>if and only if we can do this so that the resulting number is a power of two</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定正整数 <code>N</code>&nbsp;，我们按任何顺序（包括原始顺序）将数字重新排序，注意其前导数字不能为零。</p>

<p>如果我们可以通过上述方式得到&nbsp;2 的幂，返回 <code>true</code>；否则，返回 <code>false</code>。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>1
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>10
<strong>输出：</strong>false
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>16
<strong>输出：</strong>true
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>24
<strong>输出：</strong>false
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：</strong>46
<strong>输出：</strong>true
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= N &lt;= 10^9</code></li>
</ol>


## Note

##1 排列组合        

itertools.permutations



**检查一个排列是不是 2 的幂，首先需要检查有没有前置 0，再不断除 2 直到当前数为奇数。如果结果是 1，那就是 2 的幂**



##2 计数     看0-9各有多少个数字

```

class Solution {

    public boolean reorderedPowerOf2(int N) {

        int[] A = count(N);

        for (int i = 0; i < 31; ++i)

            if (Arrays.equals(A, count(1 << i)))

                return true;

        return false;

    }



    // Returns the count of digits of N

    // Eg. N = 112223334, returns [0,2,3,3,1,0,0,0,0,0]

    public int[] count(int N) {

        int[] ans = new int[10];

        while (N > 0) {

            ans[N % 10]++;

            N /= 10;

        }

        return ans;

    }

}



```








## Solution

Language: **java**  /  Runtime: 152 ms

```java
class Solution {
    public boolean reorderedPowerOf2(int N) {
        // Build eg. N = 128 -> A = [1, 2, 8]
        String S = Integer.toString(N);
        int[] A = new int[S.length()];
        for (int i = 0; i < S.length(); ++i)
            A[i] = S.charAt(i) - '0';
        return permutations(A, 0);
    }

    // Return true if A represents a valid power of 2
    public boolean isPowerOfTwo(int[] A) {
        if (A[0] == 0) return false;  // no leading zero

        // Build eg. A = [1, 2, 8] -> N = 128
        int N = 0;
        for (int x: A)
            N = 10 * N + x;

        // Remove the largest power of 2
        while (N > 0 && ((N & 1) == 0))   //N不是奇数
            N >>= 1;

        // Check that there are no other factors besides 2
        return N == 1;
    }

    /**
     * Returns true if some permutation of (A[start], A[start+1], ...)
     * can result in A representing a power of 2.
     */
    public boolean permutations(int[] A, int start) {
        if (start == A.length)
            return isPowerOfTwo(A);

        // Choose some index i from [start, A.length - 1]
        // to be placed into position A[start].
        for (int i = start; i < A.length; ++i) {
            // Place A[start] with value A[i].
            swap(A, start, i);

            // For each such placement of A[start], if a permutation
            // of (A[start+1], A[start+2], ...) can result in A
            // representing a power of 2, return true.
            if (permutations(A, start + 1))
                return true;

            // Restore the array to the state it was in before
            // A[start] was placed with value A[i].
            swap(A, start, i);
        }

        return false;
    }

    public void swap(int[] A, int i, int j) {
        int t = A[i];
        A[i] = A[j];
        A[j] = t;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reordered-power-of-2/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reordered-power-of-2/description/)

Solution: [LeetCode](https://leetcode.com/articles/reordered-power-of-2/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reordered-power-of-2/)

[回到目录](../README.md)