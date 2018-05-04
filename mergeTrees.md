# 问题
给定两个二叉树，想象当你将它们中的一个覆盖到另一个上时，两个二叉树的一些节点便会重叠。

你需要将他们合并为一个新的二叉树。合并的规则是如果两个节点重叠，那么将他们的值相加作为节点合并后的新值，否则不为 NULL 的节点将直接作为新二叉树的节点。
# 程序
```C
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
struct TreeNode* mergeTrees(struct TreeNode* t1, struct TreeNode* t2) {
    if(!t1)
        return t2;
    if(!t2)
        return t1;
    t1 -> val += t2 ->val;
    t1 -> left = mergeTrees(t1 -> left, t2 -> left);
    t1 -> right = mergeTrees(t1 ->right, t2 -> right);
    return t1;
}
```
# 心得
合并两个二叉树的时候，可以把一个树的值对应的赋在另一个树对应的值上。如果一个树为空，则可以直接返回另一个不为空的树。