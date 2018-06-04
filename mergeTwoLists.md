# 问题
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 
# 程序
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
    struct ListNode* root = node;
    node -> next = NULL;
    while(l1 != NULL || l2 != NULL){
        if(l1 == NULL)
        {
            node -> next = l2;
            return root -> next;
        } 
        else if(l2 == NULL)
        {
            node -> next = l1;
            return root -> next;
        } 
        else if(l1 -> val <= l2 -> val)
        {
            node -> next = l1;
            l1 = l1 -> next;
        } 
        else
        {
            node -> next = l2;
            l2 = l2 -> next;
        }
        node = node -> next;
    }
    return root -> next;
}
```
# 心得
新定义一个链表，如果两个链表中有一个为空，则新链表就是另一个不为空的链表；如果两个链表都不为空，则逐个比较两个链表中值的大小，新链表的节点等于小的一个链表节点，最终返回新链表。