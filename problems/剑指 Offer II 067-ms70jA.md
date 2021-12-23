# 剑指 Offer II 067. ms70jA | 最大的异或

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个整数数组 <code>nums</code> ，返回<em> </em><code>nums[i] XOR nums[j]</code> 的最大运算结果，其中 <code>0 &le; i &le; j &lt; n</code> 。</p>

<p>&nbsp;</p>

<div class="original__bRMd">
<div>
<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [3,10,5,25,2,8]
<strong>输出：</strong>28
<strong>解释：</strong>最大运算结果是 5 XOR 25 = 28.</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [0]
<strong>输出：</strong>0
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [2,4]
<strong>输出：</strong>6
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>nums = [8,10,2]
<strong>输出：</strong>10
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>nums = [14,70,53,83,49,91,36,80,92,51,66,70]
<strong>输出：</strong>127
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
</div>
</div>

<p>&nbsp;</p>

<p><strong>进阶：</strong>你可以在 <code>O(n)</code> 的时间解决这个问题吗？</p>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 421&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/maximum-xor-of-two-numbers-in-an-array/">https://leetcode-cn.com/problems/maximum-xor-of-two-numbers-in-an-array/</a></p>




## Solution

Language: **java**  /  Runtime: 129 ms

```java
class Solution {
    class TrieNode {
        TrieNode[] next = new TrieNode[2];
        public TrieNode insert(int val) {
            TrieNode node = next[val];
            if (node == null) {
                node = new TrieNode();
                next[val] = node;
            }
            return node;
        }
    }

    public int findMaximumXOR(int[] nums) {
        TrieNode root = new TrieNode();
        insert(root, nums[0]);
        int max = 0;
        for (int i = 1; i < nums.length; i++) {
            // 每次元素都在与它前面所有数构造的字典树进行异或
            max = Math.max(max, maxXOR(root, nums[i]));
            insert(root, nums[i]);
        }
        return max;
    }

    public void insert(TrieNode root, int num) {
        TrieNode node = root;
        for (int i = 30; i >= 0; i--) {
            node = node.insert((num >> i) & 1);
        }
    }

    public int maxXOR(TrieNode root, int num) {
        int ans = 0;
        TrieNode node = root;
        // 对于每一个num，只需要循环31次就能找到它与其他数最大的异或值
        for (int i = 30; i >= 0; i--) {
            int choose = (num >> i) & 1;
            if (node.next[1 - choose] != null) {
                ans |= 1 << i;
                node = node.next[1 - choose];
            } else {
                node = node.next[choose];
            }
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ms70jA/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ms70jA/description/)

Solution: [LeetCode](https://leetcode.com/articles/ms70jA/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ms70jA/)

[回到目录](../README.md)