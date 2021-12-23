# 剑指 Offer 24. fan-zhuan-lian-biao-lcof | 反转链表

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p> instead-->
<p>定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL
<strong>输出:</strong> 5-&gt;4-&gt;3-&gt;2-&gt;1-&gt;NULL</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= 节点个数 &lt;= 5000</code></p>

<p>&nbsp;</p>

<p><strong>注意</strong>：本题与主站 206 题相同：<a href="https://leetcode-cn.com/problems/reverse-linked-list/">https://leetcode-cn.com/problems/reverse-linked-list/</a></p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode newHead = reverseList(head.next);
        head.next.next = head;
        head.next = null;
        return newHead;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/fan-zhuan-lian-biao-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/fan-zhuan-lian-biao-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/fan-zhuan-lian-biao-lcof/)

[回到目录](../README.md)