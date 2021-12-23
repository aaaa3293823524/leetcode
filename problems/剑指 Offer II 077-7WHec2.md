# 剑指 Offer II 077. 7WHec2 | 链表排序

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定链表的头结点&nbsp;<code>head</code>&nbsp;，请将其按 <strong>升序</strong> 排列并返回 <strong>排序后的链表</strong> 。</p>

<ul>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/09/14/sort_list_1.jpg" style="width: 302px; " /></p>

<pre>
<b>输入：</b>head = [4,2,1,3]
<b>输出：</b>[1,2,3,4]
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/09/14/sort_list_2.jpg" style="width: 402px; " /></p>

<pre>
<b>输入：</b>head = [-1,5,3,4,0]
<b>输出：</b>[-1,0,3,4,5]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>head = []
<b>输出：</b>[]
</pre>

<p>&nbsp;</p>

<p><b>提示：</b></p>

<ul>
	<li>链表中节点的数目在范围&nbsp;<code>[0, 5 * 10<sup>4</sup>]</code>&nbsp;内</li>
	<li><code>-10<sup>5</sup>&nbsp;&lt;= Node.val &lt;= 10<sup>5</sup></code></li>
</ul>

<p>&nbsp;</p>

<p><b>进阶：</b>你可以在&nbsp;<code>O(n&nbsp;log&nbsp;n)</code> 时间复杂度和常数级空间复杂度下，对链表进行排序吗？</p>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 148&nbsp;题相同：<a href="https://leetcode-cn.com/problems/sort-list/">https://leetcode-cn.com/problems/sort-list/</a></p>




## Solution

Language: **java**  /  Runtime: 10 ms

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode sortList(ListNode head) {
        Deque<ListNode> queue = new LinkedList<>();
        while (head != null) {
            ListNode pre = head;
            head = head.next;
            pre.next = null;
            queue.offer(pre);
        }
        while (queue.size() > 1) {
            ListNode a = queue.poll();
            ListNode b = queue.poll();
            ListNode mergeNode = merge(a, b);
            queue.offer(mergeNode);
        }
        return queue.poll();
    }

    public ListNode merge(ListNode a, ListNode b) {
        ListNode dummy = new ListNode(0);
        ListNode head = dummy;
        while (a != null && b != null) {
            if (a.val < b.val) {
                head.next = a;
                a = a.next;
            } else {
                head.next = b;
                b = b.next;
            }
            head = head.next;
        }
        if (a == null && b != null) {
            head.next = b;
        } else if (a != null && b == null) {
            head.next = a;
        }
        return dummy.next;
    }
}




```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/7WHec2/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/7WHec2/description/)

Solution: [LeetCode](https://leetcode.com/articles/7WHec2/)  /  [LeetCode中国](https://leetcode-cn.com/articles/7WHec2/)

[回到目录](../README.md)