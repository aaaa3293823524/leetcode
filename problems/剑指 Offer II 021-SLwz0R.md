# 剑指 Offer II 021. SLwz0R | 删除链表的倒数第 n 个结点

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个链表，删除链表的倒数第&nbsp;<code>n</code><em>&nbsp;</em>个结点，并且返回链表的头结点。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg" style="width: 542px; height: 222px;" /></p>

<pre>
<strong>输入：</strong>head = [1,2,3,4,5], n = 2
<strong>输出：</strong>[1,2,3,5]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>head = [1], n = 1
<strong>输出：</strong>[]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>head = [1,2], n = 1
<strong>输出：</strong>[1]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>链表中结点的数目为 <code>sz</code></li>
	<li><code>1 &lt;= sz &lt;= 30</code></li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
	<li><code>1 &lt;= n &lt;= sz</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>进阶：</strong>能尝试使用一趟扫描实现吗？</p>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 19&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/">https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/</a></p>




## Solution

Language: **java**  /  Runtime: 0 ms

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(head==null)return null;
        ListNode t=head,t1=head,pre=null;;
        for(int i=0;i<n;i++) {
            t=t.next;
        }
        if(t==null)return head.next;
        while(t!=null) {
            t=t.next;
            pre=t1;
            t1=t1.next;
        }
        pre.next=t1.next;
        return head;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/SLwz0R/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/SLwz0R/description/)

Solution: [LeetCode](https://leetcode.com/articles/SLwz0R/)  /  [LeetCode中国](https://leetcode-cn.com/articles/SLwz0R/)

[回到目录](../README.md)