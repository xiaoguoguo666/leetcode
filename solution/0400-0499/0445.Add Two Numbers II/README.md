# [445. 两数相加 II](https://leetcode-cn.com/problems/add-two-numbers-ii)

[English Version](/solution/0400-0499/0445.Add%20Two%20Numbers%20II/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->
<p>给定两个<strong>非空</strong>链表来代表两个非负整数。数字最高位位于链表开始位置。它们的每个节点只存储单个数字。将这两数相加会返回一个新的链表。</p>

<p>&nbsp;</p>

<p>你可以假设除了数字 0 之外，这两个数字都不会以零开头。</p>

<p><strong>进阶:</strong></p>

<p>如果输入链表不能修改该如何处理？换句话说，你不能对列表中的节点进行翻转。</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong> (7 -&gt; 2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<strong>输出:</strong> 7 -&gt; 8 -&gt; 0 -&gt; 7
</pre>

## 解法

<!-- 这里可写通用的实现逻辑 -->

利用栈将数字逆序。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

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
            # 创建结点，利用头插法将结点插入链表
            node = ListNode(carry % 10)
            node.next = dummy.next
            dummy.next = node
            carry //= 10
        return dummy.next
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

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
            // 创建结点，利用头插法将结点插入链表
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
