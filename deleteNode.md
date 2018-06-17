# 问题
请编写一个函数，使其可以删除某个链表中给定的（非末尾）节点，你将只被给定要求被删除的节点。
# 程序
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
void deleteNode(struct ListNode* node) {
    struct ListNode *t;
    t = node -> next;
    node -> val = t -> val;
    node -> next = t -> next;
}
```
# 心得
新设定一个中间值t，指向目标节点的后一位，将后一位的值赋给节点所在的位置，这样就可以删掉目标节点值，得到想要的链表。