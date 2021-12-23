# 1755. closest-subsequence-sum | 最接近目标值的子序列和

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>nums</code> and an integer <code>goal</code>.</p>

<p>You want to choose a subsequence of <code>nums</code> such that the sum of its elements is the closest possible to <code>goal</code>. That is, if the sum of the subsequence&#39;s elements is <code>sum</code>, then you want to <strong>minimize the absolute difference</strong> <code>abs(sum - goal)</code>.</p>

<p>Return <em>the <strong>minimum</strong> possible value of</em> <code>abs(sum - goal)</code>.</p>

<p>Note that a subsequence of an array is an array formed by removing some elements <strong>(possibly all or none)</strong> of the original array.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,-7,3,5], goal = 6
<strong>Output:</strong> 0
<strong>Explanation:</strong> Choose the whole array as a subsequence, with a sum of 6.
This is equal to the goal, so the absolute difference is 0.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [7,-9,15,-2], goal = -5
<strong>Output:</strong> 1
<strong>Explanation:</strong> Choose the subsequence [7,-9,-2], with a sum of -4.
The absolute difference is abs(-4 - (-5)) = abs(1) = 1, which is the minimum.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3], goal = -7
<strong>Output:</strong> 7
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 40</code></li>
	<li><code>-10<sup>7</sup> &lt;= nums[i] &lt;= 10<sup>7</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= goal &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>nums</code> 和一个目标值 <code>goal</code> 。</p>

<p>你需要从 <code>nums</code> 中选出一个子序列，使子序列元素总和最接近 <code>goal</code> 。也就是说，如果子序列元素和为 <code>sum</code> ，你需要 <strong>最小化绝对差</strong> <code>abs(sum - goal)</code> 。</p>

<p>返回 <code>abs(sum - goal)</code> 可能的 <strong>最小值</strong> 。</p>

<p>注意，数组的子序列是通过移除原始数组中的某些元素（可能全部或无）而形成的数组。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [5,-7,3,5], goal = 6
<strong>输出：</strong>0
<strong>解释：</strong>选择整个数组作为选出的子序列，元素和为 6 。
子序列和与目标值相等，所以绝对差为 0 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [7,-9,15,-2], goal = -5
<strong>输出：</strong>1
<strong>解释：</strong>选出子序列 [7,-9,-2] ，元素和为 -4 。
绝对差为 abs(-4 - (-5)) = abs(1) = 1 ，是可能的最小值。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>nums = [1,2,3], goal = -7
<strong>输出：</strong>7
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 40</code></li>
	<li><code>-10<sup>7</sup> &lt;= nums[i] &lt;= 10<sup>7</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= goal &lt;= 10<sup>9</sup></code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 380 ms

```cpp
class Solution {
public:
    int minAbsDifference(vector<int>& nums, int goal) {
        int size = nums.size(), half = size / 2, minDiff = abs(goal);  // 子集为空
        vector<int> sums1(1 << half, 0), sums2(1 << (size - half), 0);

        getSums(nums, 0, sums1);  // 子集在前半部分
        sort(sums1.begin(), sums1.end());
        auto iter = lower_bound(sums1.begin(), sums1.end(), goal);
        if (iter != sums1.end()) {
            minDiff = min(minDiff, *iter - goal);
        }
        if (iter != sums1.begin()) {
            minDiff = min(minDiff, goal - *(--iter));
        }

        getSums(nums, half, sums2);  // 子集在后半部分
        sort(sums2.begin(), sums2.end());
        iter = lower_bound(sums2.begin(), sums2.end(), goal);
        if (iter != sums2.end()) {
            minDiff = min(minDiff, *iter - goal);
        }
        if (iter != sums2.begin()) {
            minDiff = min(minDiff, goal - *(--iter));
        }

        return min(minDiff, getMinDiff(sums1, sums2, goal));  // 子集在前后子集各取一部分合并
    }

    void getSums(vector<int>& nums, int start, vector<int>& sums) {
        int i, j, bit, size = sums.size();

        for (i = 1; i < size; ++i) {
            for (j = 0, bit = 1; bit < size; ++j, bit <<= 1) {
                if ((i & bit) != 0) {
                    sums[i] = sums[i ^ bit] + nums[j + start];
                    break;
                }
            }
        }
    }

    int getMinDiff(vector<int>& nums1, vector<int>& nums2, int goal) {
        int left = 0, right = nums2.size() - 1, size = nums1.size(), minDiff = INT_MAX;

        while (left < size && right >= 0) {
            int sum = nums1[left] + nums2[right];
            minDiff = min(minDiff, abs(sum - goal));

            if (sum == goal) {
                break;
            }
            else if (sum > goal) {
                --right;
            }
            else {
                ++left;
            }
        }

        return minDiff;
    }
};


```

Language: **java**  /  Runtime: 165 ms

```java
class Solution {
    private static void getAllSum4(int[] nums, int index, int len, int[] arr) {
        // arr[0]: 一个数也没有的, 就是 0
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < len; j++) {
                if ((i & (1<<j)) !=0 ) { // 依次考察状态 i 上的每一位上的 1
                    arr[i] = arr[i ^ (1<<j)] + nums[j + index];
                    break; // 这个 break 很重要, 提速了!!!
                }
            }
        }
    }

    public static int minAbsDifference(int[] nums, int goal) {
        if (nums == null || nums.length == 0) {
            return goal;
        }
        int half = nums.length/2;
        int[] l = new int[1 << half];
        int[] r = new int[1 << (nums.length -half)];
        getAllSum4(nums, 0, half, l);
        getAllSum4(nums, nums.length >> 1, nums.length - half, r);
        Arrays.sort(l);
        Arrays.sort(r);
        int ans = Math.abs(goal);
        // le 数组从 0 开始
        // re 数组从最大开始, 相当于双指针了
        int re = r.length-1;
        for (int i = 0; i < l.length; i++) { // 从 le 数组里取出每一个数, 到 re 里找最匹配的数
            int rest = goal - l[i];
            // 从最后一个开始, 最后一个是最大值, 必然 gap 最大
            while (re > 0 && Math.abs(rest - r[re - 1]) <= Math.abs(rest - r[re])) {
                re--;
            }
            ans = Math.min(ans, Math.abs(rest - r[re]));
        }
        return ans;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/closest-subsequence-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/closest-subsequence-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/closest-subsequence-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/closest-subsequence-sum/)

[回到目录](../README.md)