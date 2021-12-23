# 1994. the-number-of-good-subsets | 好子集的数目

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>nums</code>. We call a subset of <code>nums</code> <strong>good</strong> if its product can be represented as a product of one or more <strong>distinct prime</strong> numbers.</p>

<ul>
	<li>For example, if <code>nums = [1, 2, 3, 4]</code>:

	<ul>
		<li><code>[2, 3]</code>, <code>[1, 2, 3]</code>, and <code>[1, 3]</code> are <strong>good</strong> subsets with products <code>6 = 2*3</code>, <code>6 = 2*3</code>, and <code>3 = 3</code> respectively.</li>
		<li><code>[1, 4]</code> and <code>[4]</code> are not <strong>good</strong> subsets with products <code>4 = 2*2</code> and <code>4 = 2*2</code> respectively.</li>
	</ul>
	</li>
</ul>

<p>Return <em>the number of different <strong>good</strong> subsets in </em><code>nums</code><em> <strong>modulo</strong> </em><code>10<sup>9</sup> + 7</code>.</p>

<p>A <strong>subset</strong> of <code>nums</code> is any array that can be obtained by deleting some (possibly none or all) elements from <code>nums</code>. Two subsets are different if and only if the chosen indices to delete are different.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The good subsets are:
- [1,2]: product is 2, which is the product of distinct prime 2.
- [1,2,3]: product is 6, which is the product of distinct primes 2 and 3.
- [1,3]: product is 3, which is the product of distinct prime 3.
- [2]: product is 2, which is the product of distinct prime 2.
- [2,3]: product is 6, which is the product of distinct primes 2 and 3.
- [3]: product is 3, which is the product of distinct prime 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,2,3,15]
<strong>Output:</strong> 5
<strong>Explanation:</strong> The good subsets are:
- [2]: product is 2, which is the product of distinct prime 2.
- [2,3]: product is 6, which is the product of distinct primes 2 and 3.
- [2,15]: product is 30, which is the product of distinct primes 2, 3, and 5.
- [3]: product is 3, which is the product of distinct prime 3.
- [15]: product is 15, which is the product of distinct primes 3 and 5.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 30</code></li>
</ul>
 instead-->
<p>给你一个整数数组&nbsp;<code>nums</code>&nbsp;。如果&nbsp;<code>nums</code>&nbsp;的一个子集中，所有元素的乘积可以用若干个 <strong>互不相同的质数</strong>&nbsp;相乘得到，那么我们称它为&nbsp;<strong>好子集</strong>&nbsp;。</p>

<ul>
	<li>比方说，如果&nbsp;<code>nums = [1, 2, 3, 4]</code>&nbsp;：

	<ul>
		<li><code>[2, 3]</code>&nbsp;，<code>[1, 2, 3]</code>&nbsp;和&nbsp;<code>[1, 3]</code>&nbsp;是 <strong>好</strong>&nbsp;子集，乘积分别为&nbsp;<code>6 = 2*3</code>&nbsp;，<code>6 = 2*3</code>&nbsp;和&nbsp;<code>3 = 3</code>&nbsp;。</li>
		<li><code>[1, 4]</code> 和&nbsp;<code>[4]</code>&nbsp;不是 <strong>好</strong>&nbsp;子集，因为乘积分别为&nbsp;<code>4 = 2*2</code> 和&nbsp;<code>4 = 2*2</code>&nbsp;。</li>
	</ul>
	</li>
</ul>

<p>请你返回 <code>nums</code>&nbsp;中不同的&nbsp;<strong>好</strong>&nbsp;子集的数目对<em>&nbsp;</em><code>10<sup>9</sup> + 7</code>&nbsp;<strong>取余</strong>&nbsp;的结果。</p>

<p><code>nums</code>&nbsp;中的 <strong>子集</strong>&nbsp;是通过删除 <code>nums</code>&nbsp;中一些（可能一个都不删除，也可能全部都删除）元素后剩余元素组成的数组。如果两个子集删除的下标不同，那么它们被视为不同的子集。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>nums = [1,2,3,4]
<b>输出：</b>6
<b>解释：</b>好子集为：
- [1,2]：乘积为 2 ，可以表示为质数 2 的乘积。
- [1,2,3]：乘积为 6 ，可以表示为互不相同的质数 2 和 3 的乘积。
- [1,3]：乘积为 3 ，可以表示为质数 3 的乘积。
- [2]：乘积为 2 ，可以表示为质数 2 的乘积。
- [2,3]：乘积为 6 ，可以表示为互不相同的质数 2 和 3 的乘积。
- [3]：乘积为 3 ，可以表示为质数 3 的乘积。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>nums = [4,2,3,15]
<b>输出：</b>5
<b>解释：</b>好子集为：
- [2]：乘积为 2 ，可以表示为质数 2 的乘积。
- [2,3]：乘积为 6 ，可以表示为互不相同质数 2 和 3 的乘积。
- [2,15]：乘积为 30 ，可以表示为互不相同质数 2，3 和 5 的乘积。
- [3]：乘积为 3 ，可以表示为质数 3 的乘积。
- [15]：乘积为 15 ，可以表示为互不相同质数 3 和 5 的乘积。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 30</code></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 392 ms

```python3
mod = 10 ** 9 + 7
class Solution:
    def numberOfGoodSubsets(self, nums: List[int]) -> int:
        cnts = [0] * 31
        for n in nums:
            cnts[n] += 1
        for n in [4, 8, 9, 12, 16, 18, 20, 24, 25, 27, 28]:
            cnts[n] = 0  # 排除掉有多个相同因子的

        mutex = [0] * 31
        for i in range(2, 31):
            for j in range(2, 31):
                if i != j and gcd(i, j) > 1:
                    mutex[i] |= 1 << j

        def dfs(n, chose):  # n表示当前数字，chose的第i位标识是否选择i
            if n == 31:
                return 1 if chose > 0 else 0
            ret = dfs(n + 1, chose)
            if cnts[n] > 0 and mutex[n] & chose == 0:
                ret += cnts[n] * dfs(n + 1, chose | (1 << n))
            return ret % mod

        return dfs(2, 0) * pow(2, cnts[1], mod) % mod  # 1可以选择任意个


```

Language: **java**  /  Runtime: 375 ms

```java
public class Solution {
    int[] count;
    boolean[] isValid;
    Map<Integer, Set<Integer>> pre;
    long mod = (long) (1e9 + 7);

    public int numberOfGoodSubsets(int[] nums) {
        pre = new HashMap<>(30);
        isValid = new boolean[31];
        count = new int[31];
        for (int num : nums) {
            count[num]++;
        }
        init();
        long p = qpow(2, count[1]);
        return (int) (p * dfs(2, new HashSet<>()) % mod);
    }

    public long dfs(int num, Set<Integer> set) {
        if (num == 31) {
            if (set.size() == 0) {
                return 0;
            }
            return 1;
        }
        long res = 0;
        res = (res + dfs(num + 1, new HashSet<>(set))) % mod;
        if (isValid[num] && count[num] > 0) {
            for (int a : pre.get(num)) {
                if (set.contains(a)) {
                    return res;
                }
            }
            for (int a : pre.get(num)) {
                set.add(a);
            }
            res = (res + count[num] * dfs(num + 1, new HashSet<>(set))) % mod;
        }
        return res;
    }

    public long qpow(int x, int k) {
        if (k == 0) {
            return 1;
        }
        if ((k & 1) == 1) {
            return qpow(x, k / 2) * qpow(x, k / 2) * x % mod;
        } else {
            return qpow(x, k / 2) * qpow(x, k / 2) % mod;
        }
    }

    public void init() {
        for (int num = 1; num <= 30; num++) {
            isValid[num] = true;
            Set<Integer> set = new HashSet<>();
            int temp = num;
            for (int i = 2; i <= temp / i; i++) {
                while (temp % i == 0) {
                    temp /= i;
                    if (set.contains(i)) {
                        isValid[num] = false;
                        break;
                    }
                    set.add(i);
                }
                if (!isValid[num]) {
                    break;
                }
            }
            if (temp != 1) {
                set.add(temp);
            }
            pre.put(num, set);
        }
    }

}



```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/the-number-of-good-subsets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/the-number-of-good-subsets/description/)

Solution: [LeetCode](https://leetcode.com/articles/the-number-of-good-subsets/)  /  [LeetCode中国](https://leetcode-cn.com/articles/the-number-of-good-subsets/)

[回到目录](../README.md)