# 问题
删除链表中等于给定值 val 的所有节点。
# 程序
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* removeElements(struct ListNode* head, int val) {
    struct ListNode *p = head, *q = NULL;
    if(head == NULL)
    {
        return NULL;
    }
    while(p)
    {
        if(p -> val == val)
        {
            if(q)
            {
                q -> next = p -> next;
            }
            else
            {
                head = head -> next;
            }
        }
        else
        {
            q = p;
        }
        p = p -> next;
    }
    return head;
}
```
# 心得
定义两个链表节点，一个赋值表头，一个赋值为空，用来存储最终需要的结果链表。从链表的表头开始循环，逐个与目标值比较，如果相同，看是否是在表头；如果不同，直接将原表的值赋值给新表。