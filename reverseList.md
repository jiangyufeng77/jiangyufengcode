# 问题
反转一个单链表。
# 程序
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* reverseList(struct ListNode* head) {
    if(head == NULL)
    {
        return NULL;
    }
    struct ListNode *p = head, *q = head -> next, *t;
    while(q != NULL)
    {
        t = q -> next;
        q -> next = p;
        p = q;
        q = t;
    }
    head -> next = NULL;
    return p;
}
```
# 心得
定义三个新节点，其中有一个用于存放中间值，和交换两个数的位置类似，依靠中间值使得前面数的位置后移，得到新的反转链表。