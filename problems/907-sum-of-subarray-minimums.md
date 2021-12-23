# 907. sum-of-subarray-minimums | 子数组的最小值之和

## Question description

<!--If you want to use the English description, use <p>Given an array of integers arr, find the sum of <code>min(b)</code>, where <code>b</code> ranges over every (contiguous) subarray of <code>arr</code>. Since the answer may be large, return the answer <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [3,1,2,4]
<strong>Output:</strong> 17
<strong>Explanation:</strong> 
Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4]. 
Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1.
Sum is 17.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [11,81,94,43,3]
<strong>Output:</strong> 444
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= arr[i] &lt;= 3 * 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给定一个整数数组 <code>arr</code>，找到 <code>min(b)</code> 的总和，其中 <code>b</code> 的范围为 <code>arr</code> 的每个（连续）子数组。</p>

<p>由于答案可能很大，因此<strong> 返回答案模 <code>10^9 + 7</code></strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>arr = [3,1,2,4]
<strong>输出：</strong>17
<strong>解释：
</strong>子数组为<strong> </strong>[3]，[1]，[2]，[4]，[3,1]，[1,2]，[2,4]，[3,1,2]，[1,2,4]，[3,1,2,4]。 
最小值为 3，1，2，4，1，1，2，1，1，1，和为 17。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>arr = [11,81,94,43,3]
<strong>输出：</strong>444
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= arr.length <= 3 * 10<sup>4</sup></code></li>
	<li><code>1 <= arr[i] <= 3 * 10<sup>4</sup></code></li>
</ul>

<p> </p>


## Note

排列组合 然后取最小值



单调栈






## Solution

Language: **cpp**  /  Runtime: 192 ms

```cpp
// ans：数组A[]的连续子数组最小值之和,ans=dp[0]+dp[1]+...+dp[n-1]
// dp[i]：以A[i]结尾的子数组的最小值之和，这是重点，以A[i]为结尾，意思就是 A[1,....,i],A[2,....,i]...A[i-1,i],就是线性的。
// dp[i]=dp[i-1]+A[i]-(修正值offset)
//如果是单调递增栈的话，A[i]作为最大值，只影响最后一个组合就是本身，A[I]的最小值才为A【I】.所以直接加上就好 
// 但是如果A[i] < A[stack.top()]的话，意味着本来以A[stack.top()]为最小值的(栈顶保存的下标-栈顶第二个元素保存的下标)这些元素
//发现自己被骗了，应该以A[i]为最小值，所以
// 对A[i]之前的每个段{offset+=(A[栈顶保存的下标]-A[i])*(栈顶保存的下标-栈顶第二个元素保存的下标)}
// 单调增栈st：从st[i-1]+1一直到st[i]代表一个段，且该段的最小值恰是A[st[i]]
//举个例子，对弈[1,3,2]来说：
//第一次1入栈，dp[0] = 1，以1结尾的；ans = dp[0] = 1;这时候只有一种情况就是{1}
//第二次3 > 1;dp[1] = dp[0] + A[1];这时候以3结尾的有两种情况{1,3}，{3}，所以最小值之和是 dp[1] = 1 + 3 = 4;
//第三次 2 < 3;dp[2] = {1,3,2} , {3,2},{2};然而dp[1] = {1,3}，{3}；所以2的出现，让{3} ——> {3,2}，这里的最小值成了2；
// 所以要减去1； dp[2] = dp[1] + A[i] - 1 = 5;
//所以ans = 1 + 4 + 5 =10
class Solution {
public:
   int sumSubarrayMins(vector<int>& A) {
       const int BASE = 1e9 + 7;
       stack<int> st;
       int ans = 0, sum = 0; // sum：以A[i]结尾的子数组的ans，相当于dp[i]
       for (int i = 0; i < A.size(); ++i) {
           while (!st.empty() && A[st.top()] >= A[i]) {
               int top = st.top(); st.pop();
               int new_top = st.empty() ? -1 : st.top();
               sum += ((A[i] - A[top]) % BASE * (top - new_top) % BASE);
           }
           sum = (sum + A[i]) % BASE;
           ans = (ans + sum) % BASE;
           st.push(i);
       }
       return ans % BASE;
   }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-subarray-minimums/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-subarray-minimums/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-subarray-minimums/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-subarray-minimums/)

[回到目录](../README.md)