# 92. reverse-linked-list-ii | 反转链表 II

## Question description

<!--If you want to use the English description, use <p>Reverse a linked list from position <em>m</em> to <em>n</em>. Do it in one-pass.</p>

<p><strong>Note:&nbsp;</strong>1 &le; <em>m</em> &le; <em>n</em> &le; length of list.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, <em>m</em> = 2, <em>n</em> = 4
<strong>Output:</strong> 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;NULL
</pre>
 instead-->
<p>反转从位置 <em>m</em> 到 <em>n</em> 的链表。请使用一趟扫描完成反转。</p>

<p><strong>说明:</strong><br>
1 &le;&nbsp;<em>m</em>&nbsp;&le;&nbsp;<em>n</em>&nbsp;&le; 链表长度。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, <em>m</em> = 2, <em>n</em> = 4
<strong>输出:</strong> 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;NULL</pre>




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
    public ListNode reverseBetween(ListNode head, int m, int n) {

        // Empty list
        if (head == null) {
            return null;
        }

        // Move the two pointers until they reach the proper starting point
        // in the list.
        ListNode cur = head, prev = null;
        while (m > 1) {
            prev = cur;
            cur = cur.next;
            m--;
            n--;
        }

        // The two pointers that will fix the final connections.
        ListNode con = prev, tail = cur;

        // Iteratively reverse the nodes until n becomes 0.
        ListNode third = null;
        while (n > 0) {
            third = cur.next;
            cur.next = prev;
            prev = cur;
            cur = third;
            n--;
        }

        // Adjust the final connections as explained in the algorithm
        if (con != null) {
            con.next = prev;
        } else {
            head = prev;
        }

        tail.next = cur;
        return head;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-linked-list-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-linked-list-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-linked-list-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-linked-list-ii/)

[回到目录](../README.md)