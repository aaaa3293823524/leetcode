# 61. rotate-list | 旋转链表

## Question description

<!--If you want to use the English description, use <p>Given the <code>head</code> of a linked&nbsp;list, rotate the list to the right by <code>k</code> places.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/rotate1.jpg" style="width: 450px; height: 191px;" />
<pre>
<strong>Input:</strong> head = [1,2,3,4,5], k = 2
<strong>Output:</strong> [4,5,1,2,3]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/roate2.jpg" style="width: 305px; height: 350px;" />
<pre>
<strong>Input:</strong> head = [0,1,2], k = 4
<strong>Output:</strong> [2,0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is in the range <code>[0, 500]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
	<li><code>0 &lt;= k &lt;= 2 * 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给你一个链表的头节点 <code>head</code> ，旋转链表，将链表每个节点向右移动 <code>k</code><em> </em>个位置。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/rotate1.jpg" style="width: 600px; height: 254px;" />
<pre>
<strong>输入：</strong>head = [1,2,3,4,5], k = 2
<strong>输出：</strong>[4,5,1,2,3]
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/roate2.jpg" style="width: 472px; height: 542px;" />
<pre>
<strong>输入：</strong>head = [0,1,2], k = 4
<strong>输出：</strong>[2,0,1]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>链表中节点的数目在范围 <code>[0, 500]</code> 内</li>
	<li><code>-100 <= Node.val <= 100</code></li>
	<li><code>0 <= k <= 2 * 10<sup>9</sup></code></li>
</ul>




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
    public ListNode rotateRight(ListNode head, int k) {
        if(head==null)return null;
        int len=0;
        ListNode pre=null,cur=head,kcur=head,kpre=null;
        while(cur!=null) {
            len++;
            cur=cur.next;
        }
        k=k%len;
        if(k==0)return  head;
        cur=head;
        for(int i=0;i<k;i++) {
            //System.out.println(kcur.val);
            kcur=kcur.next;
        }
        while(kcur!=null) {
            pre=cur;
            kpre=kcur;
            kcur=kcur.next;
            cur=cur.next;
        }
        kpre.next=head;
        pre.next=null;
        return cur;
    }
}
```

Language: **python3**  /  Runtime: 56 ms

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def rotateRight(self, head: 'ListNode', k: 'int') -> 'ListNode':
        # base cases
        if not head:
            return None
        if not head.next:
            return head
        
        # close the linked list into the ring
        old_tail = head
        n = 1
        while old_tail.next:
            old_tail = old_tail.next
            n += 1
        old_tail.next = head
        
        # find new tail : (n - k % n - 1)th node
        # and new head : (n - k % n)th node
        new_tail = head
        for i in range(n - k % n - 1):
            new_tail = new_tail.next
        new_head = new_tail.next
        
        # break the ring
        new_tail.next = None
        
        return new_head

        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/rotate-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/rotate-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/rotate-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/rotate-list/)

[回到目录](../README.md)