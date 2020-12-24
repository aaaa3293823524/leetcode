# 206. reverse-linked-list | 反转链表

## Question description

<!--If you want to use the English description, use <p>Reverse a singly linked list.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL
<strong>Output:</strong> 5-&gt;4-&gt;3-&gt;2-&gt;1-&gt;NULL
</pre>

<p><b>Follow up:</b></p>

<p>A linked list can be reversed either iteratively or recursively. Could you implement both?</p>
 instead-->
<p>反转一个单链表。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL
<strong>输出:</strong> 5-&gt;4-&gt;3-&gt;2-&gt;1-&gt;NULL</pre>

<p><strong>进阶:</strong><br>
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？</p>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution{
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
        }
        return prev;
    }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-linked-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-linked-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-linked-list/)

[回到目录](../README.md)