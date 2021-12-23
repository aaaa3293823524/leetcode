# 剑指 Offer 22. lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof | 链表中倒数第k个节点

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p> instead-->
<p>输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。</p>

<p>例如，一个链表有 <code>6</code> 个节点，从头节点开始，它们的值依次是 <code>1、2、3、4、5、6</code>。这个链表的倒数第 <code>3</code> 个节点是值为 <code>4</code> 的节点。</p>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
给定一个链表: <strong>1->2->3->4->5</strong>, 和 <em>k </em><strong>= 2</strong>.

返回链表 4<strong>->5</strong>.</pre>




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
    public ListNode getKthFromEnd(ListNode head, int k) {
        //双指针
        ListNode h=head,h1=head;
        for(int i=0;i<k;i++){
            h=h.next;
        }
        while(h!=null){
            h1=h1.next;
            h=h.next;
        }
        return h1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

[回到目录](../README.md)