# 剑指 Offer 40. zui-xiao-de-kge-shu-lcof | 最小的k个数

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>输入整数数组 <code>arr</code> ，找出其中最小的 <code>k</code> 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>arr = [3,2,1], k = 2
<strong>输出：</strong>[1,2] 或者 [2,1]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>arr = [0,1,2,1], k = 1
<strong>输出：</strong>[0]</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>0 &lt;= k &lt;= arr.length &lt;= 10000</code></li>
	<li><code>0 &lt;= arr[i]&nbsp;&lt;= 10000</code></li>
</ul>


## Note

快速选择    堆


## Solution

Language: **java**  /  Runtime: 16 ms

```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        int[] vec = new int[k];
        if (k == 0) { // 排除 0 的情况
            return vec;
        }
        PriorityQueue<Integer> queue = new PriorityQueue<Integer>(new Comparator<Integer>() {
            public int compare(Integer num1, Integer num2) {
                return num2 - num1;
            }
        });
        for (int i = 0; i < k; ++i) {
            queue.offer(arr[i]);
        }
        for (int i = k; i < arr.length; ++i) {
            if (queue.peek() > arr[i]) {
                queue.poll();
                queue.offer(arr[i]);
            }
        }
        for (int i = 0; i < k; ++i) {
            vec[i] = queue.poll();
        }
        return vec;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/zui-xiao-de-kge-shu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/zui-xiao-de-kge-shu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/zui-xiao-de-kge-shu-lcof/)

[回到目录](../README.md)