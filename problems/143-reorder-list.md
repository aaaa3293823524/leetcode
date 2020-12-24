# 143. reorder-list | 重排链表

## Question description

<!--If you want to use the English description, use <p>Given a singly linked list <em>L</em>: <em>L</em><sub>0</sub>&rarr;<em>L</em><sub>1</sub>&rarr;&hellip;&rarr;<em>L</em><sub><em>n</em>-1</sub>&rarr;<em>L</em><sub>n</sub>,<br />
reorder it to: <em>L</em><sub>0</sub>&rarr;<em>L</em><sub><em>n</em></sub>&rarr;<em>L</em><sub>1</sub>&rarr;<em>L</em><sub><em>n</em>-1</sub>&rarr;<em>L</em><sub>2</sub>&rarr;<em>L</em><sub><em>n</em>-2</sub>&rarr;&hellip;</p>

<p>You may <strong>not</strong> modify the values in the list&#39;s nodes, only nodes itself may be changed.</p>

<p><strong>Example 1:</strong></p>

<pre>
Given 1-&gt;2-&gt;3-&gt;4, reorder it to 1-&gt;4-&gt;2-&gt;3.</pre>

<p><strong>Example 2:</strong></p>

<pre>
Given 1-&gt;2-&gt;3-&gt;4-&gt;5, reorder it to 1-&gt;5-&gt;2-&gt;4-&gt;3.
</pre>
 instead-->
<p>给定一个单链表&nbsp;<em>L</em>：<em>L</em><sub>0</sub>&rarr;<em>L</em><sub>1</sub>&rarr;&hellip;&rarr;<em>L</em><sub><em>n</em>-1</sub>&rarr;<em>L</em><sub>n ，</sub><br>
将其重新排列后变为： <em>L</em><sub>0</sub>&rarr;<em>L</em><sub><em>n</em></sub>&rarr;<em>L</em><sub>1</sub>&rarr;<em>L</em><sub><em>n</em>-1</sub>&rarr;<em>L</em><sub>2</sub>&rarr;<em>L</em><sub><em>n</em>-2</sub>&rarr;&hellip;</p>

<p>你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>给定链表 1-&gt;2-&gt;3-&gt;4, 重新排列为 1-&gt;4-&gt;2-&gt;3.</pre>

<p><strong>示例 2:</strong></p>

<pre>给定链表 1-&gt;2-&gt;3-&gt;4-&gt;5, 重新排列为 1-&gt;5-&gt;2-&gt;4-&gt;3.</pre>




## Solution

Language: **java**  /  Runtime: 3 ms

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
    public void reorderList(ListNode head) {
        if(head == null) return;
        ListNode slow = head, fast = head.next;
        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode right = reverse(slow.next);
        slow.next = null;
        
        ListNode left = head;
        while(right != null){
            ListNode next = right.next;
            right.next = left.next;
            left.next = right;
            right = next;
            left = left.next.next;
        }
    }
    
    ListNode reverse(ListNode head){
        ListNode prev = null;
        while(head != null){
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reorder-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reorder-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/reorder-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reorder-list/)

[回到目录](../README.md)