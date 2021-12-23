# 剑指 Offer II 026. LGjMqU | 重排链表

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个单链表 <code>L</code><em> </em>的头节点 <code>head</code> ，单链表 <code>L</code> 表示为：</p>

<p><code>&nbsp;L<sub>0&nbsp;</sub>&rarr; L<sub>1&nbsp;</sub>&rarr; &hellip; &rarr; L<sub>n-1&nbsp;</sub>&rarr; L<sub>n&nbsp;</sub></code><br />
请将其重新排列后变为：</p>

<p><code>L<sub>0&nbsp;</sub>&rarr;&nbsp;L<sub>n&nbsp;</sub>&rarr;&nbsp;L<sub>1&nbsp;</sub>&rarr;&nbsp;L<sub>n-1&nbsp;</sub>&rarr;&nbsp;L<sub>2&nbsp;</sub>&rarr;&nbsp;L<sub>n-2&nbsp;</sub>&rarr; &hellip;</code></p>

<p>不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626420311-PkUiGI-image.png" style="width: 240px; " /></p>

<pre>
<strong>输入: </strong>head = [1,2,3,4]
<strong>输出: </strong>[1,4,2,3]</pre>

<p><strong>示例 2:</strong></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626420320-YUiulT-image.png" style="width: 320px; " /></p>

<pre>
<strong>输入: </strong>head = [1,2,3,4,5]
<strong>输出: </strong>[1,5,2,4,3]</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>链表的长度范围为 <code>[1, 5 * 10<sup>4</sup>]</code></li>
	<li><code>1 &lt;= node.val &lt;= 1000</code></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 143&nbsp;题相同：<a href="https://leetcode-cn.com/problems/reorder-list/">https://leetcode-cn.com/problems/reorder-list/</a>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 2 ms

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
    public void reorderList(ListNode head) {
        ListNode fast=head,slow=head,s=head;
        while(fast.next!=null&&fast.next.next!=null) {
            fast=fast.next.next;
            slow=slow.next;
        }//slow最后一个 slow之后反转
        
        ListNode pre=null,cur=slow.next,next;
        while(cur!=null) {
            next=cur.next;
            cur.next=pre;
            pre=cur;
            cur=next;
        }//pre首部节点
        slow.next=null;
        //System.out.println(pre.val);
        // while(pre!=null){
        //     System.out.println(pre.val);
        //     pre=pre.next;
        // }
        
        // while(s!=null){
        //     System.out.println(s.val);
        //     s=s.next;
        // }
        ListNode p=pre,next1=s,next2=p;
        //System.out.println("p1:"+pre.val);
        while(p!=null){
            //System.out.println("s:"+s.val);
            //System.out.println("p:"+p.val);
            next1=s.next;
            next2=p.next;
            s.next=p;
            p.next=next1;
            s=next1;
            p=next2;
        }
        // s=head;
        // while(s!=null){
        //     System.out.println(s.val);
        //     s=s.next;
        // }
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/LGjMqU/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/LGjMqU/description/)

Solution: [LeetCode](https://leetcode.com/articles/LGjMqU/)  /  [LeetCode中国](https://leetcode-cn.com/articles/LGjMqU/)

[回到目录](../README.md)