# 86. partition-list | 分隔链表

## Question description

<!--If you want to use the English description, use <p>Given a linked list and a value <em>x</em>, partition it such that all nodes less than <em>x</em> come before nodes greater than or equal to <em>x</em>.</p>

<p>You should preserve the original relative order of the nodes in each of the two partitions.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> head = 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;2, <em>x</em> = 3
<strong>Output:</strong> 1-&gt;2-&gt;2-&gt;4-&gt;3-&gt;5
</pre>
 instead-->
<p>给定一个链表和一个特定值<em> x</em>，对链表进行分隔，使得所有小于 <em>x</em> 的节点都在大于或等于 <em>x</em> 的节点之前。</p>

<p>你应当保留两个分区中每个节点的初始相对位置。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> head = 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;2, <em>x</em> = 3
<strong>输出:</strong> 1-&gt;2-&gt;2-&gt;4-&gt;3-&gt;5
</pre>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public ListNode partition(ListNode head, int x) {

        // before and after are the two pointers used to create the two list
        // before_head and after_head are used to save the heads of the two lists.
        // All of these are initialized with the dummy nodes created.
        ListNode before_head = new ListNode(0);
        ListNode before = before_head;
        ListNode after_head = new ListNode(0);
        ListNode after = after_head;

        while (head != null) {

            // If the original list node is lesser than the given x,
            // assign it to the before list.
            if (head.val < x) {
                before.next = head;
                before = before.next;
            } else {
                // If the original list node is greater or equal to the given x,
                // assign it to the after list.
                after.next = head;
                after = after.next;
            }

            // move ahead in the original list
            head = head.next;
        }

        // Last node of "after" list would also be ending node of the reformed list
        after.next = null;

        // Once all the nodes are correctly assigned to the two lists,
        // combine them to form a single list which would be returned.
        before.next = after_head.next;

        return before_head.next;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/partition-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/partition-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/partition-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/partition-list/)

[回到目录](../README.md)