# 2. add-two-numbers | 两数相加

## Question description

<!--If you want to use the English description, use <p>You are given two <strong>non-empty</strong> linked lists representing two non-negative integers. The digits are stored in <strong>reverse order</strong>, and each of their nodes contains a single digit. Add the two numbers and return the sum&nbsp;as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg" style="width: 483px; height: 342px;" />
<pre>
<strong>Input:</strong> l1 = [2,4,3], l2 = [5,6,4]
<strong>Output:</strong> [7,0,8]
<strong>Explanation:</strong> 342 + 465 = 807.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> l1 = [0], l2 = [0]
<strong>Output:</strong> [0]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
<strong>Output:</strong> [8,9,9,9,0,0,0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in each linked list is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
	<li>It is guaranteed that the list represents a number that does not have leading zeros.</li>
</ul>
 instead-->
<p>给你两个 <strong>非空</strong> 的链表，表示两个非负的整数。它们每位数字都是按照 <strong>逆序</strong> 的方式存储的，并且每个节点只能存储 <strong>一位</strong> 数字。</p>

<p>请你将两个数相加，并以相同形式返回一个表示和的链表。</p>

<p>你可以假设除了数字 0 之外，这两个数都不会以 0 开头。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2021/01/02/addtwonumber1.jpg" style="width: 483px; height: 342px;" />
<pre>
<strong>输入：</strong>l1 = [2,4,3], l2 = [5,6,4]
<strong>输出：</strong>[7,0,8]
<strong>解释：</strong>342 + 465 = 807.
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>l1 = [0], l2 = [0]
<strong>输出：</strong>[0]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
<strong>输出：</strong>[8,9,9,9,0,0,0,1]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>每个链表中的节点数在范围 <code>[1, 100]</code> 内</li>
	<li><code>0 <= Node.val <= 9</code></li>
	<li>题目数据保证列表表示的数字不含前导零</li>
</ul>




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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
//        ListNode
        int carry=0;
        ListNode newHeadListNode=new ListNode(-1);
        ListNode s=newHeadListNode;
        while(l1!=null||l2!=null) {
            int t1=0;
            if(l1!=null){
                t1=l1.val;
                l1=l1.next;
            }
            int t2=0;
            if(l2!=null){
                t2=l2.val;
                l2=l2.next;
            }
            ListNode temp=new ListNode((t1+t2+carry)%10);
            carry=(t1+t2+carry)/10;
            s.next=temp;
            s=temp;
        }
        if(carry!=0)s.next=new ListNode(1);
        return newHeadListNode.next;
    }
}
```

Language: **python**  /  Runtime: 68 ms

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        r = ListNode(0)   
        r.val = self.cal_next(0, l1, l2, r)
        return r

    def cal_next(self, up_val, l1, l2, r):    
        val1 = l1.val if l1 else 0
        val2 = l2.val if l2 else 0    
        l1_next = l1.next if l1 else None
        l2_next = l2.next if l2 else None            
        r.val = (val1 + val2 + up_val) % 10
        up_val = (val1 + val2 + up_val) // 10           
        if l1_next or l2_next or up_val:
            r.next = ListNode(0)
            r.next.val = self.cal_next(up_val, l1_next, l2_next, r.next)     
        return r.val
```

Language: **cpp**  /  Runtime: 36 ms

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        
        ListNode* dummy = new ListNode(0);
        ListNode* curr  = dummy;
        int carry = 0;
        
        while (l1 || l2) {
            
            int val1 = l1 ? l1->val : 0;
            int val2 = l2 ? l2->val : 0;
            
            int sum = val1 + val2 + carry;
            carry = sum / 10;
            
            curr->next = new ListNode(sum % 10);
            curr = curr->next;
            
            if (l1) l1 = l1->next;
            if (l2) l2 = l2->next;
        }
        
        if (carry) curr->next = new ListNode(carry);
        
        return dummy->next;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-two-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-two-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-two-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-two-numbers/)

[回到目录](../README.md)