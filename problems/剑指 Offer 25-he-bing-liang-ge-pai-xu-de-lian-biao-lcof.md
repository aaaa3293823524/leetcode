# 剑指 Offer 25. he-bing-liang-ge-pai-xu-de-lian-biao-lcof | 合并两个排序的链表

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。</p>

<p><strong>示例1：</strong></p>

<pre><strong>输入：</strong>1-&gt;2-&gt;4, 1-&gt;3-&gt;4
<strong>输出：</strong>1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4</pre>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= 链表长度 &lt;= 1000</code></p>

<p>注意：本题与主站 21 题相同：<a href="https://leetcode-cn.com/problems/merge-two-sorted-lists/">https://leetcode-cn.com/problems/merge-two-sorted-lists/</a></p>




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
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode p=new ListNode(-1);
        ListNode s=p;
        while(l1!=null||l2!=null){
            if(l1==null){
                while(l2!=null){
                s.next=l2;
                s=s.next;
                l2=l2.next;
                }
                break;
            }
            if(l2==null){
                while(l1!=null){
                s.next=l1;
                s=s.next;
                l1=l1.next;
                }
                break;
            }
            if(l1.val<l2.val){
                s.next=l1;
                s=s.next;
                l1=l1.next;
            }else{
                s.next=l2;
                s=s.next;
                l2=l2.next;
            }
        }
        return p.next;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

[回到目录](../README.md)