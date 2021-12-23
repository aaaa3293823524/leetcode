# 904. fruit-into-baskets | 水果成篮

## Question description

<!--If you want to use the English description, use <p>You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array <code>fruits</code> where <code>fruits[i]</code> is the <strong>type</strong> of fruit the <code>i<sup>th</sup></code> tree produces.</p>

<p>You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:</p>

<ul>
	<li>You only have <strong>two</strong> baskets, and each basket can only hold a <strong>single type</strong> of fruit. There is no limit on the amount of fruit each basket can hold.</li>
	<li>Starting from any tree of your choice, you must pick <strong>exactly one fruit</strong> from <strong>every</strong> tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.</li>
	<li>Once you reach a tree with fruit that cannot fit in your baskets, you must stop.</li>
</ul>

<p>Given the integer array <code>fruits</code>, return <em>the <strong>maximum</strong> number of fruits you can pick</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> fruits = [<u>1,2,1</u>]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can pick from all 3 trees.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> fruits = [0,<u>1,2,2</u>]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can pick from trees [1,2,2].
If we had started at the first tree, we would only pick from trees [0,1].
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> fruits = [1,<u>2,3,2,2</u>]
<strong>Output:</strong> 4
<strong>Explanation:</strong> We can pick from trees [2,3,2,2].
If we had started at the first tree, we would only pick from trees [1,2].
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> fruits = [3,3,3,<u>1,2,1,1,2</u>,3,3,4]
<strong>Output:</strong> 5
<strong>Explanation:</strong> We can pick from trees [1,2,1,1,2].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= fruits.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= fruits[i] &lt; fruits.length</code></li>
</ul>
 instead-->
<p>你正在探访一家农场，农场从左到右种植了一排果树。这些树用一个整数数组 <code>fruits</code> 表示，其中 <code>fruits[i]</code> 是第 <code>i</code> 棵树上的水果 <strong>种类</strong> 。</p>

<p>你想要尽可能多地收集水果。然而，农场的主人设定了一些严格的规矩，你必须按照要求采摘水果：</p>

<ul>
	<li>你只有 <strong>两个</strong> 篮子，并且每个篮子只能装 <strong>单一类型</strong> 的水果。每个篮子能够装的水果总量没有限制。</li>
	<li>你可以选择任意一棵树开始采摘，你必须从 <strong>每棵</strong> 树（包括开始采摘的树）上 <strong>恰好摘一个水果</strong> 。采摘的水果应当符合篮子中的水果类型。每采摘一次，你将会向右移动到下一棵树，并继续采摘。</li>
	<li>一旦你走到某棵树前，但水果不符合篮子的水果类型，那么就必须停止采摘。</li>
</ul>

<p>给你一个整数数组 <code>fruits</code> ，返回你可以收集的水果的 <strong>最大</strong> 数目。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>fruits = [<em><strong>1,2,1</strong></em>]
<strong>输出：</strong>3
<strong>解释：</strong>可以采摘全部 3 棵树。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>fruits = [0,<em><strong>1,2,2</strong></em>]
<strong>输出：</strong>3
<strong>解释：</strong>可以采摘 [1,2,2] 这三棵树。
如果从第一棵树开始采摘，则只能采摘 [0,1] 这两棵树。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>fruits = [1,<em><strong>2,3,2,2</strong></em>]
<strong>输出：</strong>4
<strong>解释：</strong>可以采摘 [2,3,2,2] 这四棵树。
如果从第一棵树开始采摘，则只能采摘 [1,2] 这两棵树。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>fruits = [3,3,3,<em><strong>1,2,1,1,2</strong></em>,3,3,4]
<strong>输出：</strong>5
<strong>解释：</strong>可以采摘 [1,2,1,1,2] 这五棵树。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= fruits.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= fruits[i] &lt; fruits.length</code></li>
</ul>


## Note

滑动窗口


## Solution

Language: **java**  /  Runtime: 68 ms

```java
class Solution {
    public int totalFruit(int[] tree) {
        int ans = 0, i = 0;
        Counter count = new Counter();
        for (int j = 0; j < tree.length; ++j) {
            count.add(tree[j], 1);
            while (count.size() >= 3) {
                count.add(tree[i], -1);
                if (count.get(tree[i]) == 0)
                    count.remove(tree[i]);
                i++;
            }

            ans = Math.max(ans, j - i + 1);
        }

        return ans;
    }
}

class Counter extends HashMap<Integer, Integer> {
    public int get(int k) {
        return containsKey(k) ? super.get(k) : 0;
    }

    public void add(int k, int v) {
        put(k, get(k) + v);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/fruit-into-baskets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fruit-into-baskets/description/)

Solution: [LeetCode](https://leetcode.com/articles/fruit-into-baskets/)  /  [LeetCode中国](https://leetcode-cn.com/articles/fruit-into-baskets/)

[回到目录](../README.md)