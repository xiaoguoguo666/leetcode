# [445. Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii)

[中文文档](/solution/0400-0499/0445.Add%20Two%20Numbers%20II/README.md)

## Description

<p>You are given two <b>non-empty</b> linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p><b>Follow up:</b><br />

What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

</p>

<p>

<b>Example:</b>

<pre>

<b>Input:</b> (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)

<b>Output:</b> 7 -> 8 -> 0 -> 7

</pre>

</p>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        s1, s2 = [], []
        while l1:
            s1.append(l1.val)
            l1 = l1.next
        while l2:
            s2.append(l2.val)
            l2 = l2.next
        carry, dummy = 0, ListNode(-1)
        while s1 or s2 or carry:
            carry += (0 if not s1 else s1.pop()) + (0 if not s2 else s2.pop())
            node = ListNode(carry % 10)
            node.next = dummy.next
            dummy.next = node
            carry //= 10
        return dummy.next
```

### **Java**

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        Deque<Integer> s1 = new ArrayDeque<>();
        Deque<Integer> s2 = new ArrayDeque<>();
        for (; l1 != null; l1 = l1.next) {
            s1.push(l1.val);
        }
        for (; l2 != null; l2 = l2.next) {
            s2.push(l2.val);
        }
        int carry = 0;
        ListNode dummy = new ListNode(-1);
        while (!s1.isEmpty() || !s2.isEmpty() || carry != 0) {
            carry += (s1.isEmpty() ? 0 : s1.pop()) + (s2.isEmpty() ? 0 : s2.pop());
            ListNode node = new ListNode(carry % 10);
            node.next = dummy.next;
            dummy.next = node;
            carry /= 10;
        }
        return dummy.next;
    }
}
```

### **...**

```

```

<!-- tabs:end -->
