# 问题
给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。
# 程序
```C
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* deleteDuplicates(struct ListNode* head) {
    if(head == NULL)
        return head;
    struct ListNode *p = head;
    while(p -> next != NULL)
    {
        if(p -> val == p ->next ->val)
        {
            p ->next = p ->next ->next;
        }
        else
        {
            p = p ->next;
        }
    }
    return head;
}
```
# 心得
当指针不为空时，如果指针当前所指的数和下一个数相同，则将下下个数的值赋值到下个数，然后指针后移一位；否则指针直接指向下一位。