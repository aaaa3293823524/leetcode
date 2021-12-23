# 19. remove-nth-node-from-end-of-list | 删除链表的倒数第 N 个结点

## Question description

<!--If you want to use the English description, use <p>Given the <code>head</code> of a linked list, remove the <code>n<sup>th</sup></code> node from the end of the list and return its head.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg" style="width: 542px; height: 222px;" />
<pre>
<strong>Input:</strong> head = [1,2,3,4,5], n = 2
<strong>Output:</strong> [1,2,3,5]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> head = [1], n = 1
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> head = [1,2], n = 1
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is <code>sz</code>.</li>
	<li><code>1 &lt;= sz &lt;= 30</code></li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
	<li><code>1 &lt;= n &lt;= sz</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you do this in one pass?</p>
 instead-->
<p>给你一个链表，删除链表的倒数第&nbsp;<code>n</code><em>&nbsp;</em>个结点，并且返回链表的头结点。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg" style="width: 542px; height: 222px;" />
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

<p><strong>进阶：</strong>你能尝试使用一趟扫描实现吗？</p>




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
    public ListNode removeNthFromEnd (ListNode head, int n) {
        // write code here
        //if(head.next==null)return null;
        ListNode pre=head,cur=head,newHead=new ListNode(-1),pree=newHead;
        newHead.next=head;
        for(int i=0;i<n-1;i++){
            cur=cur.next;
        }
        //if(cur==head&&head.next==null)return null;
        while(cur.next!=null){
            pree=pre;
            pre=pre.next;
            cur=cur.next;
        }
        pree.next=pre.next;
        return newHead.next;
    }
}
```

Language: **cpp**  /  Runtime: 0 ms

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if (n == 0) return NULL;
        ListNode* front = head;
        ListNode* back = head;
        int currNum = 0;
        while (front != NULL) {
            front = front -> next;
            if (currNum > n) {
                back = back -> next;
            }
            currNum ++;
        }
        if (currNum == n) { //删除第一个
            return head->next;
        }
        back-> next = back->next->next;
        return head;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-nth-node-from-end-of-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-nth-node-from-end-of-list/)

[回到目录](../README.md)