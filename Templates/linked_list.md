# Linked List 

- Each node object must hold at least two pieces of information. 
	1. the node must contain the list item itself (i.e. data field). 
	2. each node must hold a reference to the next node.

## Tips and Template

- Traverse a linked list

    ```python
    node = root
    while node:
        print(node.val)
        node = node.next
    ```

- When we talk about linked list, we are normally talk about singly linked list. There is also a Doubly Linked list defined as follows:

    ![Leetcode Linked List Learn Doubly Linked List](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/04/17/screen-shot-2018-04-17-at-161130.png)

    ```python
    class Node
        def __init__(self, val):
            self.val = val
            self.prev = None
            self.next = None
    ```

- Linked list in-place operation can be confusing (i.e. insert or delete), its better to ***draw the structure*** and it'll become much more obvious 

    For example when deleting a node in the middle :

    ![Leetcode Linked List Learn Delete Operation](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/04/26/screen-shot-2018-04-26-at-203640.png)

    ```python
    node = self.get_node(index)
    prev_node = node.prev
    next_node = node.next
    prev_node.next = next_node
    next_node.prev = prev_node
    ```

- Its better to use a ***Dummy head*** most of time, especially when deleting node is required

    For example:

    ```python
    def linked_list(root):
        dummy = Node("x")
        dummy.next = root

        # Do your logic here

        return dummy.next
    ```

- In many cases, you need to track the previous node of the current node.

    ```python
    dummy = Node("x")
    dummy.next = root

    prev = dummy
    node = head

    while node:
        prev = node
        node = node.next
    ```

- ***Two pointer*** approach is widely used in linked list, such as detecting cycle, remove n-th node etc

    For example when detecting cycle:
    ```python
    def hasCycle(self, head: ListNode) -> bool:
        slow = head
        fast = head
        
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            
            if slow == fast:
                return True
            
        return False
    ```

- It is common to use ***Hashmap or hashset*** to store visited nodes, its widely use to find intersection or beginning of cyclic linked list

    ```python
    def detectCycle(self, head: ListNode) -> ListNode:
        visited = set()
        while head:
            if head.next in visited:
                return head.next
            visited.add(head)
            head = head.next
        return
    ```


Here is a great comparison of ***time complexity*** between the linked list and the array from Leetcode.

![Leetcode Linked List Learn Conclusion](https://assets.leetcode.com/uploads/2020/10/02/comparison_of_time_complexity.png)


Reference:

- [Leetcode Introduction to Linked List](https://leetcode.com/explore/learn/card/linked-list/)


Practice:

- Basic questions:
    - [707. Design Linked List](https://leetcode.com/problems/design-linked-list/)
    - [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
    - [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
    - [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

- Tricky questions:
    - [142. Linked List Cycle II - Find linked list cycle start point](https://leetcode.com/problems/linked-list-cycle-ii/)
    - [430. Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)
    - [138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)
